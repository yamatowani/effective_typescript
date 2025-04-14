# Effective TypeScript 読書メモ
## 第一章 TypeScriptとは何か
### 項目1 TypeScriptとJavaScript
- TypeScriptはJavaScriptのスーパーセットである
  - 全てのJavaScriptはTypeScriptであるが、全てのTypeScriptがJavaScriptな訳ではない
- TypeScriptの型システムはJavaScriptの実行時の動作をモデリングした静的な型システムであり、実行時に例外を投げるであろうコードを検出する
  - 型チェッカーをパスしても実行時に例外が投げられることがある
- TSは間違った引数の数で関数を呼び出すなど、例外は投げられないものの疑わしいJSのコードを許容しない
- 型アノテーションはTSにプログラマーの意図を伝え、TSが正しいコードを見分けるのに役立つ
```ts
// エラーにならない
const x = 2 + '3'
// エラーになる
const a = null + 7
const b = [] + 12
```
