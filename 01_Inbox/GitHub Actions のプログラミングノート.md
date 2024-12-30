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
- [ ] ワークフローのコードの冒頭に「ワークフローの目的や影響範囲」を記載しておくこと！
	- [ ] なぜこのワークフローが存在しているのか？
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
- [ ] `GITHUB_TOKEN` は最小権限で定義できているか？
	- [ ] パーミッションはジョブレベルで定義すること
- [ ] ワークフローの発動条件を絞る
	- [ ] イベントのフィルタリング＋Glob
	- [ ] アクティビティタイプの指定
- [ ] （必要に応じて）言語のセットアップ
	- [ ] バージョン指定にバージョンファイルを使用しているか？
- [ ] デフォルトシェルの設定
	- [ ] パイプエラー検知（Bash の `pipefail` オプションの有効化）のために、シェル指定は明示的にすべき！
- [ ] タイムアウトの設定
	- [ ] `timeout-minutes: 10` など
- [ ] 古いワークフローの自動キャンセルの設定
	- [ ] `concurrency:` の指定
- [ ] ターミナルで `actionlint` コマンドを実行し、実装したワークフローのコードを静的解析・検証する

## 良いワークフローのコードのテンプレート
```YAML
# なにをするワークフローか手短に記述
#
# ワークフローの目的や影響範囲、参考URLなどを数行で書く。
# 実装詳細ではなく、コードから読み取れない背景情報を中心にする。

name: Example
on:
  # 動作確認しやすいように手動起動をサポート
  workflow_dispatch:
  # プルリクエストはファイルパスでフィルタリング
  pull_request:
    paths: [".github/workflows/**.yml", ".github/workflows/**.yaml"]

# ワークフローレベルでパーミッションをすべて無効化
permissions: {}

# デフォルトシェルでパイプエラーを有効化
defaults:
  run:
    shell: bash

# ワークフローが複数起動したら自動キャンセル
concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

jobs:
  example:
  # もっとも安価なUbuntuランナーを利用
  runs-on: ubuntu-latest
  # 6時間も待たされないようにタイムアウトを設定
  timeout-minutes: 5
  # ジョブレベルで必要最小限のパーミッションを定義
  permissions:
    contents: read
  steps:
    # アクションはコミットハッシュで固定
    - name: Checkout
    uses: actions/checkout@eef61447b9ff4aafe5dcd4e0bbf5d482be7e7871 # v4.2.1

    # Bashトレーシングオプションの有効化でログを詳細化
    - name: Run actionlint
      run: |
        set -x
        docker run --rm -v "$(pwd):$(pwd)" -w "$(pwd)" rhysd/actionlint:1.7.3

```

## メモ
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
- ローテーション
	- 現在のクレデンシャルを無効化（または削除）し、新しいクレデンシャルを生成すること
