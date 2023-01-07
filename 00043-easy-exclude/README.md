# 解説

- 組み込みの Utility Types である `Exclude<UnionType, ExcludedMembers>` を再現する問題
  - https://www.typescriptlang.org/docs/handbook/utility-types.html#excludeuniontype-excludedmembers
- [Conditional Types](https://www.typescriptlang.org/docs/handbook/2/conditional-types.html)の特性として、Union が与えられた場合にはそれぞれの型について分岐が適用される[Distributive Conditional Types](https://www.typescriptlang.org/docs/handbook/2/conditional-types.html#distributive-conditional-types)がある
  - このとき式の結果として `never` を返すとその型は除外される
- 今回は `Exclude` の実装なので、 `U` に一致する場合に `never` を返すことで実現できる
