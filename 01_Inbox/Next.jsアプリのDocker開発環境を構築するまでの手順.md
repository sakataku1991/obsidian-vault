## やること

1. 自身の開発 PC の作業ディレクトリ（ `workspace` ディレクトリ）内に、今回作成するプロジェクト用のディレクトリを新規作成する
	- `mkdir furusato`
2. ターミナルで、作成したプロジェクト用のディレクトリの中に移動する
	- `cd furusato`
3. git の初期化をする
	- `git init`
4. 初回の空コミットをする
	- `git commit --allow-empty -m "first commit"`
5. Node.js のバージョン管理ツールと Node.js のバージョンを設定する
	- `volta list node`
	- `volta install node@20.x.x`
	- `volta pin node@20.x.x`
	- `node -v`
	- `volta list pnpm`
	- `volta install pnpm@10.x.x`
	- `volta pin pnpm@20.x.x`
	- `pnpm -v`
6. フロントエンドのアプリを管理する用のディレクトリを新規作成する
	- `mkdir frontend`
7. ターミナルで、作成したプロジェクト用のディレクトリの中に移動する
	- `cd frontend`
8. Next アプリを新規作成する
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
9. 作成した Next アプリのディレクトリの中に移動する
	- `cd tax`
10. Node.js のバージョンを設定する
	- `volta pin node@20.x.x`
	- `node -v`
11. Next アプリを起動する
	- `pnpm dev`
12. 

