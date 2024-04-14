# prettier-plugin-curly-collision

Reproduction for https://github.com/JoshuaKGoldberg/prettier-plugin-curly/issues/386.

Input:

```ts
import { Agent } from "node:http";
import { access } from "node:fs";

function test() {
  const a = true;

  if (a) return;
}
```

Expected output:

```ts
function test() {
  const a = true;

  if (a) {
    return;
  }
}
```

With `prettier-plugin-organize-imports` and `prettier-plugin-curly` (The order of the plugins matters)

```ts
import { Agent } from "node:http";
import { access } from "node:fs";

function test() {
  const a = true;

  if (a) {
    return;
  }
}
```

With `prettier-plugin-curly` and `prettier-plugin-organize-imports`

```ts
function test() {
  const a = true;

  if (a) return;
}
```
