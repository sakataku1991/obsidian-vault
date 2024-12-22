## 初期設定
- 設定ファイル
	- `~/Library/Application Support/Code/User/settings.json`
- 設定内容

```json
{

"css.lint.unknownAtRules": "ignore", // VSCodeのエラー「Unknown at rule @apply」を非表示にする

"editor.accessibilitySupport": "off", // VSCodeの効果音をOFFにする

"editor.codeActionsOnSave": {

"source.addMissingImports": "explicit", // import文を自動追加する

"source.fixAll.eslint": "explicit", // ファイル保存時にESLintを実行する

"source.fixAll.stylelint": "explicit", // ファイル保存時にStylelintを実行する

"source.organizeImports": "explicit", // 使用していないimport文を自動削除する＆abc順にソートする

},

"editor.codeLens": false, // フォーカス中のコードのReferenceを非表示にする

"editor.cursorBlinking": "phase", // カーソルの点滅アニメーションをなめらかにする

"editor.cursorSmoothCaretAnimation": "explicit", // カーソル移動にアニメーションを付与する

"editor.defaultFormatter": "esbenp.prettier-vscode", // デフォルトのフォーマッター

"editor.fontFamily": "SourceHanMono-Regular, Menlo, Monaco, 'Courier New', monospace", // エディターのフォントファミリー

"editor.fontSize": 15, // エディターのフォントサイズ

"editor.formatOnSave": true, // ファイル保存時の自動フォーマットを有効化する

"editor.guides.bracketPairs": true, // エディター上のコードにホバーすると勝手に出てくるツールチップを非表示にする

"editor.inlineSuggest.enabled": true, // エディター上でインライン候補を自動的に表示する

"editor.linkedEditing": true, // 拡張機能『Auto Rename Tag』を有効化し、HTMLのタグ名の変更を開始タグと閉じタグとで連動させる

"editor.minimap.enabled": false, // ミニマップを非表示にする

"editor.renderFinalNewline": "dimmed", // ファイルの末尾にある空行の行番号を、薄い文字で表示する

"editor.renderLineHighlight": "all", // エディター上の行へのフォーカス時のハイライト、左端の「行番号」の部分も含めてハイライトさせる

"editor.renderLineHighlightOnlyWhenFocus": true, // エディターにフォーカスしていない時は、行のハイライトをしないようにする

"editor.stickyScroll.enabled": false, // VSCodeの「スティッキー スクロール」機能を無効化する（なんか行が勝手に固定化されるやつ）

"editor.tabSize": 2, // エディターのインデントのサイズ

"editor.wordSeparators": "`~!@#$%^&*()=+[{]}\\|;:'\",.<>/?", // エディターでセパレーターとして扱う文字（`-` だけ除外している）

"editor.wordWrap": "on", // エディター上に長い行のコードがあり、右にはみ出そうな場合、行の終端で折り返すスタイルで表示させる

"explorer.confirmDelete": false, // ファイル削除時に出てくる確認モーダルを非表示にする

"explorer.confirmDragAndDrop": false, // ファイルのドラッグ＆ドロップ時に出てくる確認モーダルを非表示にする

"files.autoSave": "afterDelay", // ファイルの自動保存機能の設定

"files.insertFinalNewline": true, // ファイルの最後に必ず1行分の空行を残す

"files.trimFinalNewlines": true, // ファイルの最後に必ず1行分の空行を残す

"git.openRepositoryInParentFolders": "never", // ワークスペース（VSCodeで開いているフォルダー）の中でGitリポジトリが入れ子になっている場合、親フォルダー内と開いているファイルのどちらでリポジトリを開くようにするかの設定

"liveServer.settings.donotShowInfoMsg": true, // 拡張機能『Live Server』使用時の、インフォメッセージのポップアップを非表示にする

"markdown.preview.fontSize": 15, // マークダウンプレビューのフォントサイズ

"security.workspace.trust.untrustedFiles": "open", // 信頼されたワークスペース上で、そのワークスペース外のファイルを開く際のふるまいの制御

"terminal.integrated.defaultProfile.osx": "fish", // 規定のターミナル プロファイルの設定

"terminal.integrated.enableMultiLinePasteWarning": "never", // ターミナルに複数行のコードをコピペしようとすると出てくる警告モーダルを非表示にする

"terminal.integrated.fontSize": 14, // ターミナルのフォントサイズ

"window.commandCenter": false, // ウィンドウ上部・中央のコマンドセンターを非表示にする

"window.zoomLevel": -1, // VSCodeのウィンドウ全体のズーム レベルの設定

"workbench.colorTheme": "Monokai", // VSCodeの配色テーマ

"workbench.editor.enablePreview": false, // ファイルを開く際、常に新しいタブで開かれるようにする

"workbench.editor.tabSizing": "fixed", // ファイル名のタブのサイズを固定サイズにする

"workbench.editorAssociations": {

"*.log": "default" // 通常のテキストエディターで `.log` ファイルを開くようにする

}, // VSCode左側にあるアクティビティバーの「製品アイコン」のテーマ

"workbench.layoutControl.enabled": false, // VSCodeのウィンドウ右上にある「レイアウト コントロール」のアイコンを非表示にする

"workbench.tree.indent": 22,

"prettify-ts.maxDepth": 4, // VSCodeで開いているフォルダーの「ファイルツリー」のインデントのサイズ
}

```

## インストールする拡張機能
- 
