# 解説

- [Indexed Access Types](https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html)を利用して、先頭要素の型は `T[0]` で取得できる
- これで解決のように思われるが、これだけでは空配列が渡された場合に動作しない
- TypeScript では[Conditional Types](https://www.typescriptlang.org/docs/handbook/2/conditional-types.html)と呼ばれる所謂三項演算子の記法で条件分岐させることができる
  - 元配列が空配列 `[]` である場合には `never` を返し、それ以外では `T[0]` とすることですべての場合に対応できることになる
