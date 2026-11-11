# Shared build cache

Run this action on a runner with network access to the private cache. It configures
sccache WebDAV and Gradle HTTP caching without distributing a cloud or cache key.
It does not install sccache, Gradle, a compiler or a JDK.

```yaml
permissions:
  contents: read
  id-token: write
steps:
  # Pin this action to the reviewed full commit SHA.
  - uses: elide-dev/.github/actions/setup-build-cache@<commit-sha>
    with:
      endpoint: ${{ vars.BUILD_CACHE_ENDPOINT }}
      namespace: v1
```

The action starts an authenticated loopback relay for the job. It refreshes GitHub
OIDC tokens automatically and removes the relay and its temporary Gradle init
script at job end. The gateway checks the signed issuer, audience, immutable owner
and repository IDs, event and ref. Each repository/ref has its own cache indexes;
branches and PRs can fall back to `main`, but cannot write into its index. Fork
jobs stay on hosted runners under their repository's existing trust policy.

Gradle's local cache remains enabled, with an additional remote `HttpBuildCache`.
The init script reads only job environment variables and preserves existing
`GRADLE_USER_HOME` and credentials. The relay's HTTP address is loopback; the
upstream HTTP origin must be a private IPv4 address, or use HTTPS. Private HTTP
is intended for the GCP VPC, not an Internet-facing cache.

For a WebDAV-enabled sccache build, the action exports `SCCACHE_WEBDAV_ENDPOINT`,
username/password, `RW_MODE=READ_WRITE` and `DISABLE_CREATE_DIR=true`. sccache and
Gradle retain their native object compression; bytes are not recompressed by the
HTTP relay. Configure `RUSTC_WRAPPER=sccache` or your compiler launcher separately.
Stop an already-running sccache server before changing backend configuration, and
remove competing backend settings (such as `SCCACHE_GHA_ENABLED`) explicitly;
this action does not silently override unrelated cache backends.

`gradle: 'false'` skips the init script. `namespace` versions opaque object keys.
By default, an unreachable private endpoint leaves existing settings untouched;
`required: 'true'` makes setup failure fail the job. `enabled` reports success and
`ELIDE_BUILD_CACHE_ENABLED=true` is exported only after identity verification.
A later cache outage follows each client's normal remote-cache failure behavior.
Use a WebDAV-enabled sccache release supporting `SCCACHE_WEBDAV_DISABLE_CREATE_DIR`.

Both protocols use a small HTTP-to-REAPI gateway on the cache node: opaque keys
map to upstream BuildBuddy Action Cache entries, and payload bytes live in the
same Buildbarn hot CAS as Bazel inputs. Successful PUT acknowledges only after
upstream CAS and index writes complete. Local SSD loss causes cold reads, not
loss of acknowledged objects, subject to the upstream cache's normal eviction.
Metrics and service logs flow through the cloud OTel gateway to Datadog.

Validation: `node --test actions/setup-build-cache/relay.test.cjs`.
