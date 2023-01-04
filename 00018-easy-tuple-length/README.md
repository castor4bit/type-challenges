# 概要

- まず、引数の型が Tuples であることを保証するために `<T>` を `<T extends readonly any[]>` とする
- Tuples は`length`を持つ Array と同様のインターフェースを持つと解説されているので、[Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)により `T['length]` で長さ情報にアクセスできる
