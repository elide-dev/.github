
<center>
<img src="https://static.elide.dev/assets/org-profile/creative/elide-banner-purple.png" alt="Elide" />

<br />
<blockquote>
elide: verb. to omit (a sound or syllable) when speaking. to join together; to merge.
</blockquote>
<br />
</center>

<br />

<p>
Elide is a new runtime and framework designed for the polyglot era.
</p>

<p>
<b>Mix and match languages including JavaScript, Python, Ruby, and JVM</b>, with the ability to share objects between them.
</p>

<p>
<b>It's fast:</b> Elide can execute Python at up to <b>3x</b> the speed of CPython, Ruby at up to <b>22x</b> vs. CRuby, and JavaScript at up to <b>75x</b> the speed of Node. Elide already beats Node, Deno, and Bun under benchmark.
</p>

<br />
<ul>
    <li><b>Visit <a href="https://elide.dev">elide.dev</a></b>, our website, which runs on Elide</li>
    <li><b>Watch the <a href="https://www.youtube.com/watch?v=Txl9ryfbCw4">launch video</a></b> for demos, benchmarks, and a full feature tour</li>
    <li><b>Join the devs on <a href="https://elide.dev/discord">Discord</a></b>, we are always open to new ideas and feedback</li>
</ul>
<br />

<h2>How it works</h2>

<p>
Through the power of <a href="https://graalvm.org">GraalVM</a>, your app can do all this without a network border, without an IPC border, and without resorting to additional runtimes like Node. Elide provides utilities and a polyglot command line interface on top of GraalVM, so you can drop your app in and go.
</p>

<h2>It's a runtime</h2>

<p>Elide is a <i>runtime</i> in the sense that you can use it to run your code. Elide supports standard APIs, and strives for compliance with the <a href="https://wintercg.org">WinterCG</a> baseline. Elide provides reasonable Node API compatibility where it makes sense to do so.</p>

<h3>Installation:</h3>

<b>In one line</b> (macOS and Linux):
```
curl -sSL --tlsv1.2 elide.sh | bash -s -
```

<b>Or, via Homebrew:</b>

```
brew tap elide-dev/elide
brew install elide
```

<b>Or, via Docker:</b>

```
docker run --platform linux/amd64 --rm ghcr.io/elide-dev/elide
```

<b>Then you can do:</b>
<pre>
> elide run your-app-written-in.js
// or
> elide run your-app-written-in.py
// or
> elide shell --javascript
// or
> elide shell --python
</pre>

<h2>It's a framework</h2>

<p>Elide is a <i>framework</i> in the sense that you can use it to assemble an app, from your code.</p>

<b>Use it from Gradle (Kotlin DSL):</b>
```properties
# gradle.properties
elideVersion = 1.0.0-alpha7
```

```kotlin
// settings.gradle.kts
dependencyResolutionManagement {
  versionCatalogs {
    create("framework") {
      from("dev.elide:elide-bom:$elideVersion")
    }
  }
}

// build.gradle.kts
dependencies {
  implementation(framework.elide.core)
  // or
  implementation("dev.elide:elide-core:1.0.0-alpha7")
}
```

<b>Use it from Maven:</b>
```xml
<dependency>
  <groupId>dev.elide</groupId>
  <artifactId>elide-core</artifactId>
  <version>1.0.0-alpha7</version>
</dependency>
```

👆 This would install the [`elide-core`](https://docs.elide.dev/apidocs/packages/core/index.html) module, which provides cross-platform (pure-Kotlin) utilities.
