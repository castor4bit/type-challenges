# 解説

- 組み込みのUtility Typesである `Readonly<Type>` を再現する問題
  - https://www.typescriptlang.org/docs/handbook/utility-types.html#readonlytype
- 型宣言で `readonly` を付加するとそのプロパティは上書き不可となる
- あとは各キーに対してreadonlyを再設定すればよいので、[00004-easy-pick](./00004-easy-pick/)と同様に[Mapped Types](https://www.typescriptlang.org/docs/handbook/2/mapped-types.html)と[Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)を利用して型定義する