# 解説

- [Tuple](https://www.typescriptlang.org/docs/handbook/2/objects.html#tuple-types)の各要素を Object にマッピングする問題
  - Tuple は配列の一種だが、要素に対する型の位置と個数が固定化されているもの
  - `(string|number)[]` は文字列または数値で任意の長さの配列だが、`[string, number]` は長さが 2 で文字列->数値の順に並んでいる必要がある
- [Mapped Types](https://www.typescriptlang.org/docs/handbook/2/mapped-types.html)を利用して各要素に対して型定義を行うのはこれまでの問題と同様のパターン
- 配列要素の型取得は[Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)の特殊な記法である `T[number]` を用いることで実現できる
- ここまでで一応目的は達成されるはずだが、最後のテストケースである `@ts-expect-error` がまだ残る
- Object のキーは文字列（文字列に変換可能な値を含む）または Symbol であるので、元の tuple の要素もこれらの型に制限する必要がある
  - `keyof` は Object のプロパティを返すが、`keyof any`は指定可能な全てな型を示す `string | number | symbol` が返るのでこれを利用するのがよい
  - ES5 型定義で `declare type PropertyKey = string | number | symbol;` とされているのでこれも利用できるが、これは内部の型定義なので前者のほうが TypeScript の記法としては適切な気もする
