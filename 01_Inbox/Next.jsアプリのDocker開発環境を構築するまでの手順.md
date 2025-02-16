## やること

1. 自身の開発 PC の作業ディレクトリ（ `workspace` ディレクトリ）内に、今回作成するプロジェクト用のディレクトリを新規作成する
	- `mkdir furusato`
2. VS Code で、作成したプロジェクト用のディレクトリを開く
	- `code furusato`
3. VS Code でターミナルを開く
	- `⌘ command + T`
4. VS Code のターミナルで Node.js のバージョン管理ツールと Node.js のバージョンを設定する
	- `volta list node`
	- `volta install node@20.x.x`
	- `volta pin node@20.x.x`
	- `node -v`
	- `volta list pnpm`
	- `volta install pnpm@10.x.x`
	- `volta pin pnpm@10.x.x`
	- `pnpm -v`
5. git の初期化をする
	- `git init`
6. 初回の空コミットをする
	- `git commit --allow-empty -m "first commit"`
7. フロントエンドのアプリを管理する用のディレクトリを新規作成する
	- `mkdir frontend`
8. ターミナルで、作成したプロジェクト用のディレクトリの中に移動する
	- `cd frontend`
9. Next アプリを新規作成する
	- `npx create-next-app@latest`
	- 設定項目
		- What is your project named?: `tax`
		- Would you like to use TypeScript?: `Yes`
		- Would you like to use ESLint?: `Yes`
		- Would you like to use Tailwind CSS?: `Yes`
		- Would you like your code inside a `src/` directory?: `Yes`
		- Would you like to use App Router? (recommended): `Yes`
		- Would you like to use Turbopack for `next dev`?: `Yes`
		- Would you like to customize the import alias (`@/*` by default)?: `No`
10. 作成した Next アプリのディレクトリの中に移動する
	- `cd tax`
11. 念のため pnpm を使って Node.js パッケージを改めてインストールする
	- `pnpm i`
12. Next アプリを起動する（アプリが起動できるかどうかの確認）
	- `pnpm dev`
13. アプリが起動できることを確認できたら、アプリを停止する
	- `⌃ control + C`
14. `docker init` コマンドを実行し、 Next アプリの Docker ファイルを自動生成する
	- `docker init`
		- 設定項目
			- What application platform does your project use?: `Node`
			- What version of Node do you want to use?: `22.12.0`
				- ↑ このアプリで使用する Node.js のバージョンの数字が表示される。問題なければそのまま Enter キーを押す。
			- Which package manager do you want to use?: `pnpm`
			- What version of pnpm do you want to use?: `10.4.0`
				- ↑ このアプリで使用する pnpm のバージョンの数字が表示される。問題なければそのまま Enter キーを押す。
			- Do you want to run "pnpm run build" before starting your server?: `No`
			- What command do you want to use to start the app?: `pnpm dev`
			- What port does your server listen on?: `3000`
15. 自動生成した Docker ファイルを元に、 Docker イメージをビルドする
	- `docker compose build --no-cache`
16. Docker コンテナを起動し、 Next アプリが起動することを確認する
	- `docker compose up`

