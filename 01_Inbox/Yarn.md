## 概要
- `Node.js` 用のパッケージ管理ツール

## 初期設定
1. ターミナルで以下のコマンドを実行し、`Yarn`（LTS版）をインストールする。

```Shell
volta install yarn
```

2. インストール済みの `Yarn` の一覧を確認する。

```Shell
volta list yarn
```

`Yarn` のバージョンが一覧表示され、その中に `Yarn`（LTS版）が含まれていればOK。

`v4.5.3 (current @ /Users/sakataku1991/package.json)`

※ちなみにバージョン番号に `(current)` が付いていれば、そのバージョンが今現在グローバルに適用されている `Yarn` のバージョンということである。

3. ターミナルで以下のコマンドを実行し、Yarn のバージョンを固定する。

`$ volta pin yarn@<Yarn のバージョン番号>`

`例）`  
`$ volta pin yarn@4.5.3`

```Shell
volta pin yarn@
```

4. バージョンを確認する。

```Shell
yarn -v
```
