# 解説

- 組み込みのUtility Typesである `Pick<Type, Keys>` を再現する問題
  - https://www.typescriptlang.org/docs/handbook/utility-types.html#picktype-keys
- 定義するべきキーの一覧は `K(Keys)` で渡されるので、[Mapped Types](https://www.typescriptlang.org/docs/handbook/2/mapped-types.html)を利用して `[P in K]` で各キーに対しての型定義を行うことができる
- キーに対応する型定義は元のTodo型から参照する必要があるが、これは[Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)と呼ばれる `Todo['title]` のような記述を用いて `T[P]` として表現できる 
- ここまでで指定したキーに対する抽出は実現されるが、存在しないキーが指定されると動作しない
- Keysに相当する部分はTypeのいずれかのキーが指定されることになるので、ジェネリクスで型を制限するためにextendsを使用する
  - https://typescriptbook.jp/reference/generics/type-parameter-constraint
- Keysには元の型定義に存在するキーのみが指定できるので[keyof](https://www.typescriptlang.org/docs/handbook/2/keyof-types.html)ssでキーの一覧をstringのUnionとして取得して指定する