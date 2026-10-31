# Xの動画を保存（PWA）

XのポストURLを貼ると、動画を画質を選んで保存できるWebアプリ。サーバ不要で、GitHub Pagesにそのまま置ける。

## 公開手順（GitHub Pages）
1. GitHubで新しいリポジトリを作る（例: `x-video-save`、Public）
2. このフォルダの中身（index.html ほか全ファイル）をリポジトリ直下にアップロード
3. Settings → Pages → Source を「Deploy from a branch」、Branch を `main` / `/(root)` にして Save
4. 1〜2分後に `https://<ユーザー名>.github.io/x-video-save/` で開ける

## ホーム画面に追加
- iPhone: Safariで開く → 共有 → 「ホーム画面に追加」
- Android: Chromeで開く → メニュー → 「アプリをインストール」
  （インストール後はXの共有メニューからこのアプリへ直接URLを送れる）

## 仕組み
- ポスト情報: 公開API `api.fxtwitter.com`（失敗時は `api.vxtwitter.com`）
- 動画本体: `video.twimg.com` から直接取得（Refererを送らないことで取得可能にしている）
- iPhone/Android: 共有メニュー経由で写真アプリへ保存 / PC: そのままダウンロード

## 制約
- 鍵アカウント・削除済みポストは取得不可
- 上記の公開APIが止まると動かない（2系統あるので片方の停止には耐える）
