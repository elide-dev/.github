
<center>
<img src="https://static.elide.dev/assets/org-profile/creative/elide-banner-purple.png" alt="Elide" />
</center>

<p align="center">
  <a href="https://bestpractices.coreinfrastructure.org/projects/7690"><img src="https://bestpractices.coreinfrastructure.org/projects/7690/badge" /></a>
  <a href="https://elide.dev/discord"><img src="https://img.shields.io/discord/1119121740161884252?b1&logo=discord&logoColor=white&label=Discord" /></a>
  <a href="https://262.ecma-international.org/13.0/"><img src="https://img.shields.io/badge/-ECMA2024-blue.svg?logo=javascript&logoColor=white" /></a>
  <a href="https://typescriptlang.org"><img src="https://img.shields.io/badge/-TypeScript-blue.svg?logo=typescript&logoColor=white" /></a>
  <img alt="Python 3.11.x" src="https://img.shields.io/badge/Python%203.11.x-green?style=flat&logo=python&logoColor=white&color=blue">
  <a href="https://pkl-lang.org"><img src="https://img.shields.io/badge/-Apple%20Pkl-blue.svg?logo=apple&logoColor=white" /></a>
</p>

---

<b>Elide is like Node or Python. Use it to run things:</b>
```shell
> elide ./my-code.{ts,js,py}
```

<b>You can use Node APIs. You can even mix languages:</b>
```typescript
// sample.mts

// use node apis
import { readFileSync } from "node:fs"

// interoperate across languages 
import sample from "./sample.py"

// this is typescript - no build step needed first, like deno or bun
const x: number = 42;

console.log(sample.greeting() + ` The answer is ${x}`);
```
```python
# sample.py

def greeting(name = "Elide"):
  return f"Hello, {name}!"
```

```shell
> elide ./sample.mts
Hello, Elide! The answer is 42
```

Read more about Elide's [feature highlights](https://elide.dev)

## Installation

> [!IMPORTANT]
> Careful! Elide is in beta.

You can install Elide on Linux (amd64) or macOS (amd64/arm64) by running:

```shell
curl -sSL --tlsv1.2 elide.sh | bash -s -
```

After installation, you can run `elide --help` or `elide info` to see more information.

### Using Elide via Docker

We provide a container image, hosted on GitHub:

```
docker run --rm -it ghcr.io/elide-dev/elide
```

### Using Elide from Gradle

We provide an experimental [Gradle plugin](https://github.com/elide-dev/gradle) which can:

- Accelerate `javac` compilations by up to 20x (drop-in!) with identical inputs and outputs
- Accelerate downloading of Maven dependencies

The plugin documentation explains how it works. By native-image compiling tools like `javac`, JIT warmup is skipped, potentially yielding significant performance gains for projects under 10,000 classes.

[Installation in Gradle](https://github.com/elide-dev/gradle)
```kotlin
plugins {
  alias(elideRuntime.plugins.elide)
}
```

### Using Elide in GitHub Actions

We provide a [setup action](https://github.com/marketplace/actions/setup-elide):

```yaml
- name: "Setup: Elide"
  uses: elide-dev/setup-elide@v2
  with:
    # any tag from the `elide-dev/releases` repo; omit for latest
    version: 1.0.0-beta1
```

### Using Elide via GitHub Codespaces

We provide a [GitHub Codespace](https://github.com/features/codespaces) with Elide pre-installed. You can click below to try it out, right from your browser:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/elide-dev/elide?devcontainer_path=.devcontainer%2Fdevcontainer.json)

[1]: https://kotlinlang.org/
[2]: https://graalvm.org/
[3]: https://micronaut.io/
[4]: https://reactjs.org/
[5]: https://developers.google.com/protocol-buffers
[6]: https://grpc.io/
[7]: https://developers.google.com/closure
[8]: https://bazel.build/
[9]: https://gradle.org/
[10]: https://developers.google.com/speed/pagespeed/module
[11]: https://github.com/sgammon/elide/tree/master
[12]: https://github.com/sgammon/elide
[13]: https://buf.build
[14]: https://esbuild.github.io/
