<!-- YAML
added: v0.5.5
changes:
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18395
    description: Removed `noAssert` and no implicit coercion of the offset
                 and `byteLength` to `uint32` anymore.
-->

* `value` {integer} 要写入 `buf` 的数值。
* `offset` {integer} 开始写入之前要跳过的字节数。必须满足：`0 <= offset <= buf.length - byteLength`。
* `byteLength` {integer} 要写入的字节数。必须满足：`0 < byteLength <= 6`。
* 返回: {integer} `offset` 加上已写入的字节数。

将 `value` 中的 `byteLength` 个字节写入到 `buf` 中指定的 `offset` 位置。
最高支持 48 位精度。
当 `value` 不是无符号的整数时，行为是未定义的。

```js
const buf = Buffer.allocUnsafe(6);

buf.writeUIntBE(0x1234567890ab, 0, 6);

console.log(buf);
// 打印: <Buffer 12 34 56 78 90 ab>

buf.writeUIntLE(0x1234567890ab, 0, 6);

console.log(buf);
// 打印: <Buffer ab 90 78 56 34 12>
```

