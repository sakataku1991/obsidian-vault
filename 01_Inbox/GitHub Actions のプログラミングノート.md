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
- [ ] ワークフロー実行名（`run-name`）の設定
	- [ ] ワークフローの一覧に、ワークフローそのものの名前とワークフローを実行した GitHub アカウントの名前をセットで表示したりできるようになる
		- [ ] `run-name: Run by @${{ github.actor }}`
