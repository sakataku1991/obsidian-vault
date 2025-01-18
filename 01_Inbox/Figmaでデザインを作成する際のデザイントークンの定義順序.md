## デザイントークンの定義順序

1. 色（`color`）
2. タイポグラフィ
	- フォントファミリー
	- 文字サイズ
	- フォントウェイト
	- 行間
	- 文字間
3. 対応デバイス（デザイン作成時の前提サイズ）
4. レスポンシブ対応のブレークポイント
5. 要素の重なり順（`elevation`）
	- 重なり順序（`z-index``）
	- 影（`box-shadow`）
6. ボーダー（`border`）
	- 線の太さ
	- 線の種類
	- 線の色
7. 角丸（`shape`）
	- 角の丸み（`border-radius`）

## コンポーネントのプロパティ
- 状態（`State`）
	- UI Stack
		- 理想的な状態（`Ideal state`）
		- 初期状態（`Blank state`） or （`Initial state`）
		- ロード中の状態（`Loading state`）
		- エラーの状態（`Error state`）
		- 不完全な状態（`Partial state`）
	- ホバー時（`Hover`）
	- クリック時／タップ時（`Pressed` , `Active`）
	- フォーカス時（`Focused`）
	- 非活性時（`Disabled`）
- 種類（`Type`）
- デバイス（`Device`）
	- スマホ（`SP`）
	- タブレット（`TB`）
	- PC（`PC`）
- 権限（`Role`）
- 必須 or 任意（`is-required`）
- 活性 or 非活性（`is-active`）
- 訪問済み or 未訪問（`is-visited`）
- ログイン済み or 未ログイン（`is-logged-in`）
- 無効 or 有効（`is-disabled`）
- 既読 or 未読（`is-read`）



