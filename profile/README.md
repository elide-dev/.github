
<center>
<img src="https://static.elide.dev/assets/org-profile/creative/elide-banner-purple.png" alt="Elide" />
</center>

<p align="center">
  <a href="https://elide.dev/discord"><img src="https://img.shields.io/discord/1119121740161884252?b1&logo=discord&logoColor=white&label=Discord" /></a>
  <a href="https://262.ecma-international.org/13.0/"><img src="https://img.shields.io/badge/-ECMA2024-blue.svg?logo=javascript&logoColor=white" /></a>
  <a href="https://typescriptlang.org"><img src="https://img.shields.io/badge/-TypeScript-blue.svg?logo=typescript&logoColor=white" /></a>
  <img alt="Python 3.11.x" src="https://img.shields.io/badge/Python%203.11.x-green?style=flat&logo=python&logoColor=white&color=blue">
  <a href="https://pkl-lang.org"><img src="https://img.shields.io/badge/-Pkl-blue.svg?logo=apple&logoColor=white" /></a>
  <a href="https://kotlinlang.org"><img src="https://img.shields.io/badge/-Kotlin-blue.svg?logo=kotlin&logoColor=white" /></a>
</p>

---

<b>Elide is like Node or Python. Use it to run things:</b>
```shell
> elide ./my-code.{ts,js,py,kts,kt}
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

Learn more at [`elide.dev`](https://elide.dev)

Access the docs at [`elide.help`](https://elide.help)
