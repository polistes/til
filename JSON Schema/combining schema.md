### combining schema
JSON SchemaのWebサイトでも独立したページがある: https://json-schema.org/understanding-json-schema/reference/combining.html

type指定には複数の型を記載することができ、記載した複数の型に対してどういった条件を満たすかを更に指定することができる。
使用できるのは`anyOf`, `allOf`, `oneOf`の3つ

#### anyOf
指定した方のいずれか1つ以上に合致するかどうかを記載することができる。

単純な例だとこんな感じで、複数のデータ型を記載できる。
```
{
  "anyOf": [
    {"type": "string"},
    {"type": "integer"}
  ]
}
```
`1`や`"hoge"`といった文字列は合致するけれど、`["hoge"]`など配列に入れたりするとだめ。

`oneOf`や`allOf`といった指定も可能で、ざっくり次のような違いがある
|:-----|:-----|
|`oneOf`|指定されたtypeのうち、ちょうど1つに合致する|
|`anyOf`|指定されたtypeのうち、1つ以上に合致する|
|`allOf`|指定されたtypeの、全てに合致する|

#### 参考: Multiple Types
JSON SchemaはMultiple Typesをサポートしていると思っていて、複数の型を指定するだけであれば`{"type": ["string", "integer"]}`といった記述ができる。
`oneOf`とほぼ同等の記述だと思う。
