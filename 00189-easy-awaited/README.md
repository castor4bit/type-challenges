# 解説

- 型定義の引数?として渡された型を抽出する問題
- このパターンは [Inferring Within Conditional Types](https://www.typescriptlang.org/docs/handbook/2/conditional-types.html#inferring-within-conditional-types)としてドキュメントでも解説されている
  - Conditional Types において `infer` キーワードを用いると条件分岐にパターンを列挙することなく型推論により代替できる
  - つまり `type FlattenNumberArray<Type> = Type extends Array<number> ? number : Type` と書かれるものを `type Flatten<Type> = Type extends Array<infer Item> ? Item : Type` と一般化できる
- 設問は `Promise` に渡された型を抽出するので `T extends Promise<infer U> ? U : never` と書ける
- ところがテストケースには Promise が何重にもなっているパターンが存在するため、抽出された型が `Promise` であれば再度型抽出を行うように `T extends Promise<infer U> ? (U extends Promise<any> ? MyAwaited<U> : U) : never` とする
- 更に、関数の形式で渡されることもあるようなので同形式のパターンにも対応する
  - 愚直に関数定義をなぞってもよいが、この関数定義は TypeScript の型定義で `PromiseLike` として定義済みなのでこれを利用しすると簡潔に記述できる
    - https://github.com/microsoft/TypeScript/blob/main/lib/lib.es5.d.ts#:~:text=interface%20PromiseLike%3CT%3E
  - 本来は内部仕様のような型定義を利用するべきではない気もするが、このあと入力型を制限するために欲しくなるので使ってしまう
- ここまでで正常系のテストケースは通過するが、最後の `@ts-expect-error` にあるように `Promise` 以外の型では型不一致としたいため、引数を `T extends PromiseLike<any>` として `PromiseLike` のみ受け付けるようにする
