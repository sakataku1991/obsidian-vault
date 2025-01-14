### コードブロックのテンプレート
`$ write command here`
```Shell
write command here
```

### キーリピート（キーの連続入力）を有効化する
`$ sudo defaults write -g ApplePressAndHoldEnabled -bool false`
```Shell
sudo defaults write -g ApplePressAndHoldEnabled -bool false
```

### 無駄な `.DS_Store` ファイルを生成しないようにする①
`$ defaults write com.apple.desktopservices DSDontWriteNetworkStores true`
```Shell
defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

### 無駄な `.DS_Store` ファイルを生成しないようにする②
`$ defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true DSDontWriteNetworkStores true`
```Shell
defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true
```

### 「選択したウインドウを取り込む」で生成されるスクリーンショット画像に陰影部分を含めないようにする
`$ defaults write com.apple.screencapture disable-shadow -boolean true killall SystemUIServer`
```Shell
defaults write com.apple.screencapture disable-shadow -boolean true killall SystemUIServer
```

