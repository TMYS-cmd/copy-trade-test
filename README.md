# copy-trade-test

FXコピートレードLPの公開・デプロイ専用リポジトリです。

## 概要

このリポジトリは Netlify と連携しており、`_approved/` ディレクトリの内容が公開サイトとしてデプロイされます。また、GitHub Pages を利用してLPの管理ダッシュボードを提供します。

## ダッシュボードURL

https://tmys-cmd.github.io/copy-trade-test/

## ディレクトリ構成

- `_approved/`: 承認済み。Netlifyによって公開されるLP。
- `pages/`: 生成直後のLPが格納される作業ディレクトリ（レビュー・承認待ち）。
- `docs/`: ダッシュボード（GitHub Pages）のソース。

## ⚠️ 注意事項

- **このリポジトリ内のHTMLファイルを直接編集しないでください。**
- すべての操作（生成・承認）は `copy-trade-core` リポジトリのスクリプトまたはダッシュボードの GitHub Actions を経由して行う必要があります。

## 詳細

運用の詳細や技術仕様については、`copy-trade-core/docs/GUIDE.md` を参照してください。
