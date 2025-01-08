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
	- 検証値 ＋ 期待値
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



