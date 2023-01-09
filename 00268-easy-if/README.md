# 解説

- 条件分岐の実装となるので [Conditional Types](https://www.typescriptlang.org/docs/handbook/2/conditional-types.html) を利用する
- `C` に対して `true` と比較することで一般的な `if` 条件と同等になる
- `C` は真偽値のみ受け付けるようにするため `If<C extends boolean, T, F>` としておく
