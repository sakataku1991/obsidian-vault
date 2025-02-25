### コードブロックのテンプレート
`$ write command here`
```Shell
write command here
```

## テストの構成要素
### 基本的なテストの形式
```TypeScript
test(テストタイトル, テスト関数);
```

- テストタイトル
	- テストの内容を平易に表すタイトルを書く
- テスト関数
	- 「アサーション」を書く
	- アサーション: 「検証値が期待値どおりである」という検証を行なう文のこと

### アサーションの構成要素
- アサーション
	- 検証値 ＋ 期待値 のこと
	- expect 関数 ＋ マッチャー（ toBe など）
- マッチャー（期待値）
	- toBe （等価比較）
- テストグループ
	- テストのまとまり、グルーピングのこと
	- describe 関数
	- describe の中でさらに describe を入れ子（ネスト）にすることもできる
		- あんまりネストを深くしても見辛い＆保守しづらいテストコードになりそう
		- 「テストコードのネストは第二階層まで」などのルールを決めた方がよさそう

## おすすめ拡張機能
- VS Code の拡張機能『[Jest Runner](https://marketplace.visualstudio.com/items?itemName=firsttris.vscode-jest-runner)』
	- ↑インストールしてみたけど、「Run | Debug」のボタンが表示されない...

## テストのポイント
- プログラムにおいて、「条件分岐」に起因するバグが発生しがち
	- そのためこの「条件分岐」に着目してテストを書くことが大事！

## 思ったこと
- 「テストコード」とは、「実際に動くコードに対応した、動くドキュメントである」
- 「動くコード」を書くのと同時進行で「テストコード」も書くことで、「動くコード」の精度を高めることができる
	- 「テストコード」を書くことで強制的に様々な条件を網羅するはめになることから、パターンやケースの漏れ防止になる

## フロントエンドにおける「ユニットテスト」
- 主に、 JavaScript のコード検証をするためにテストコードが書かれる
- HTML や CSS はユニットテストの対象外？

## 閾値と例外処理
- 例外処理（エラーのスロー）
	- 例外処理は、 TypeScript の「型注釈（静的型付け）」 である程度担保できる
		- 型注釈＝入力値の制約（開発者向けのバリデーション）
- 閾値
	- 閾値に関しては、ランタイムに例外をスローする処理の実装が必要！

## マッチャーの種類
- 等価比較
	- `toBe()`
- 例外スロー
	- `toThrow()`
- 「真偽値」の検証
	- 値が「真（ `true` ）」である
		- `toBeTruthy()`
	- 値が「偽（ `false` ）」である
		- `toBeFalsy()`
- 値が `null` である
	- `toBeNull()`
- 値が `undefined` である
	- `toBeUndefined()`
	- もしくは
	- `.not.toBeDefined()`
- 「数値」の検証
	- 等価比較
		- `toBe()`
		- もしくは
		- `toEqual()`
	- 大なり比較（「検証値（ `expect()` ）」は「期待値（後述）」より大きい）
		- `toBeGreaterThan()` ←「検証値」>「期待値」
		- `toBeGreaterThanOrEqual()` ←「検証値」>=「期待値」
	- 小なり比較（「検証値」は「期待値」より小さい）
		- `toBeLessThan()` ←「検証値」<「期待値」
		- `toBeLessThanOrEqual()` ←「検証値」<=「期待値」
	- 小数計算
		- `toBeCloseTo(0.3)`
- 「文字列」の検証
	- 等価比較
		- `toBe()`
		- もしくは
		- `toEqual()`
	- 文字列の部分一致
		- `toContain("xxx")`
	- 正規表現
		- `toMatch(/^[0-9a-zA-Z]*$/)` ←この正規表現は「半角英数字」
	- 文字列の長さ
		- `toHaveLength(10)`
	- （オブジェクトに含まれる「文字列」の）部分一致
		- `stringContaining(xxx)`
	- （オブジェクトに含まれる「文字列」の）正規表現
		- `stringMatching(/^[0-9a-zA-Z]*$/)`
- 「配列」の検証
	- 特定のプリミティブが含まれているか
		- `toContain("Jest")`
	- 配列要素数の検証
		- `toHaveLength(5)`
	- 配列に特定のオブジェクトが含まれているか
		- `toContainEqual(article1)`
	- 配列に「引数に与えた配列要素」がすべて含まれているか
		- `arrayContaining([article1, article3]))`
- 「オブジェクト」の検証
	- プロパティの部分一致
		- `toMatchObject({ name: "taroyamada", age: 38 })`
	- 特定のプロパティが存在するか
		- `toHaveProperty("name")`
	- 「オブジェクト」に含まれる「オブジェクト」の検証（オブジェクト内のオブジェクト。オブジェクトの入れ子。）
		- `objectContaining({ name: "taroyamada" })`


## 「非同期処理」のテスト
- 「非同期処理」の用語
	- そもそも「非同期処理」とは？
		- あるタスクを実行をしている際に、他のタスクが別の処理を実行できる方式のこと
		- シングルスレッドながら、実行中のタスクの完了を待たずに、ほかの割り込みタスクを実行できるようにすること
	- `Promise`
		- お約束
		- 「非同期処理の完了（もしくは失敗）の結果およびその結果の値」のこと
	- `resolve`
		- 非同期処理が正常終了したことを知らせるメソッド
	- `reject`
		- 非同期処理が異常終了したことを知らせるメソッド
	- `async` 関数
		- 非同期関数を定義する関数宣言のこと
	- `await` 関数
		- `async function` 内で `Promise` の結果（ `resolve` 、 `reject` ）が返されるまで待機する（処理を一時停止する）演算子のこと

