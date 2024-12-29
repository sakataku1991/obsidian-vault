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