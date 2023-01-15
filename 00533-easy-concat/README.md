# 解説

- TypeScript 4.0 から導入された[Variadic Tuple Types](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-0.html#variadic-tuple-types)ではジェネリクス型をスプレッド構文で可変長タプルに渡すことができる
- この機能の詳細やサンプルは[機能追加時の Pull Request](https://github.com/microsoft/TypeScript/pull/39094)で多く解説されている
  - `concat` の実現はこのサンプルでもまさに同じものが記載されている
  - タプルに対する `concat` は `Array` をスプレッド構文で合成するのと同じ考えで `[...T, ...U]` のように記述すればよい
- 入力の型をタプルに限定するために `T extends any[]` のようにしておく
