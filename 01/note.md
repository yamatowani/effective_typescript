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

### 項目2 TypeScriptOption
#### noImplicitAnyオプション
- ある変数の型が不明な場合のTSの振る舞いを制御する
オフの場合はエラーにならないが、オンの場合はエラーになる
```ts
function add(a, b) {
  return a + b;
}
```
上記のような暗黙のany(implicit any)を許容するかどうかのオプション
下記のように型を宣言すれば解決する
```ts
function add(a: number, b: number) {
  return a + b;
}
```
可能な限りnoImplicitAnyは有効にしておくべき
#### strictNullChecks
- nullやundefinedが全ての型の値として許容されるべきかを制御する
- オフの場合はエラーにならないが、オンの場合はエラーになる
```ts
const x: number = null
```
nullやundefinedを許容したい場合は明記する。
```ts
const x: number | null = null
```
nullを許容したくないなら、nullが何に起因するのかを特定しチェックかアサーションを加えなければならない。
```ts

const element = document.getElementById('status')
element.textContent = 'Ready'

if (element) { // if文による絞り込み
  element.textContent = 'Ready'
}

element!.textContent = 'Ready' // 非nullアサーション
```
#### その他オプション
- デフォルトでstrictモードになっている
  - noImplicitAnyやstrictNullChecksガオンになっている
- TypeScriptコンパイラは言語のコアな部分に影響する設定を持つ
- tsconfig.jsonを使用してTSを設定する
- JS->TSに移行するときはnoImplicitAnyはオンにする
- strictをオンにすることが目標
