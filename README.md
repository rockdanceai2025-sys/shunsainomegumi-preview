# 旬彩の恵 LP ― 確認用サイト

お客様に確認していただくための、**パスワード付き公開ページ**です。

- 公開URL：<https://rockdanceai2025-sys.github.io/shunsainomegumi-preview/>
- パスワード：`shunsai2026`
- LPの元データ（制作用）：非公開リポジトリ `rockdanceai2025-sys/shunsainomegumi`

## 仕組み

このリポジトリは公開設定ですが、**LPの中身は暗号化した状態で置いてあります**（`site.bin`）。

1. お客様がURLを開くと、パスワード入力画面が出る
2. 正しいパスワードを入れたときだけ、ブラウザの中で復号されてLPが表示される
3. パスワードを知らない人は、URLを開いても入力画面しか見えない

`site.bin` を直接ダウンロードしても、パスワードなしでは中身を取り出せません
（AES-256-GCM、鍵はパスワードから PBKDF2-SHA256／25万回で生成）。

検索対策として `noindex` と `robots.txt` も入れてあるため、Google等の検索結果には出ません。

## ファイル構成

```
.
├── index.html   … パスワード入力ページ（復号して表示する処理も含む）
├── site.bin     … 暗号化したLP一式（index.html／sitemap.html／mp4.mp4）
├── robots.txt   … 検索エンジンよけ
└── .nojekyll    … GitHub Pages がファイルをそのまま配信するための設定
```

## 内容を更新するとき

LPの修正は非公開リポジトリ `shunsainomegumi` 側で行い、
このリポジトリには暗号化したものを置き直します。Claude に依頼すれば作り直します。

## パスワードを変えるとき

Claude に「確認用ページのパスワードを〇〇に変えて」と伝えてください。
`site.bin` を作り直して差し替えます（お客様には新しいパスワードの再連絡が必要です）。

## 確認が終わったら

このリポジトリは公開設定のため、確認が終わったら
GitHubの **Settings → General → Danger Zone → Delete this repository** で
削除するか、**Settings → Pages → サイトを非公開にする** で公開を止めてください。
