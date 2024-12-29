### コードブロックのテンプレート
`$ write command here`
```Shell
write command here
```

## GitHub Actions とは？
- GitHub が提供する汎用的なワークフローエンジンのこと

## GitHub Actions でできること
- 自動テスト
- 自動ビルド
- 自動デプロイ
- Issue や PR への自動アサイン

## GitHub Actions におけるタスクの単位
- 「ワークフロー（`Workflows`）」という単位でタスクを自動化することができる
- ワークフローは YAML ファイル（`.yml`）で定義する
- この YAML ファイルは `.github/workflows` ディレクトリ直下に配置すること
- ファイル名は自由に付けて OK

## 新しい GitHub Actions のワークフローを作成する際に必ず設定しておきたいこと
- [ ] `Actions secrets and variables` の `Secrets` > `Repository secrets` への以下の設定
	- [ ] `ACTIONS_STEP_DEBUG`
		- [ ] Name: ACTIONS_STEP_DEBUG
		- [ ] Secret: true
	- [ ] `ACTIONS_RUNNER_DEBUG`
		- [ ] Name: ACTIONS_RUNNER_DEBUG
		- [ ] Secret: true
- [ ] ジョブ名とステップ名（`name:`）の設定
	- [ ] 設定しておくと GitHub Actions のログが見やすくなる
- [ ] 適切なパーミッション（`permissions`）の設定
- [ ] ワークフローの発動条件を絞る
	- [ ] イベントのフィルタリング＋Glob
	- [ ] アクティビティタイプの指定
- [ ] タイムアウトの設定

## 注意点のメモ
- パーミッション、ソースコードの読み込みは暗黙的に許可されている
	- 何らかのパーミッションを記述する際には、ソースコードの読み込みにも明示的な許可が必要になってくる！
```YAML
    permissions:
      pull-requests: write
      contents: read # ←`pull-requests` （PR操作）のパーミッションを設定したいのであれば、 `contents` （ソースコード操作）を別途明示的に記述しないといけない！
```
- GitHub Actions 作成時、パーミッション関係でエラーになってしまうことがよくあるらしい
	- 使用しているアクションの README で必要なパーミッションを確認しよう！
- アクション
	- `actions/checkout`
		- リポジトリからソースコードを取得する
- ワークフローの発動条件の設定方法
	- イベントのフィルタリング
		- `paths`
			- 指定したファイルパスのみ
		- `paths-ignore`
			- 指定したファイルパス以外
		- `branches`
			- 指定したブランチのみ
		- `branches-ignore`
			- 指定したブランチ以外
		- `tags`
			- 指定した Git タグのみ
		- `tags-ignore`
			- 指定した Git タグ以外
	- Glob
	- アクティビティタイプ
		- `types: [opened, edited]`
	- if 文
