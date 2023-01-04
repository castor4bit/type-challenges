# 概要

- まず、引数の型が Tuples であることを保証するために `<T>` を `<T extends readonly any[]>` とする
- Tuples は`length`を持つ Array と同様のインターフェースを持つと[解説されている](https://www.typescriptlang.org/docs/handbook/2/objects.html#tuple-types:~:text=Other%20than%20those%20length%20checks%2C%20simple%20tuple%20types%20like%20these%20are%20equivalent%20to%20types%20which%20are%20versions%20of%20Arrays%20that%20declare%20properties%20for%20specific%20indexes%2C%20and%20that%20declare%20length%20with%20a%20numeric%20literal%20type.)ので、[Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)により `T['length]` で長さ情報にアクセスできる
