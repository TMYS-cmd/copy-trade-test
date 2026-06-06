# copy-trade-test

FXコピートレードLPの公開・デプロイ専用リポジトリです。

## 概要

このリポジトリは Netlify と連携しており、`_approved/` ディレクトリの内容が公開サイトとしてデプロイされます。また、GitHub Pages を利用してLPの管理ダッシュボードを提供します。

## ダッシュボードURL

https://tmys-cmd.github.io/copy-trade-test/

## ディレクトリ構成

- `_approved/`: 承認済み。Netlifyによって公開されるLP。
- `_staging/`: レビュー中。ステージング環境へ転送されたLP。
- `_feedback/`: 却下された際の修正指示（YAML形式）。
- `pages/`: 生成直後のLPが格納される作業ディレクトリ。
- `docs/`: ダッシュボード（GitHub Pages）のソース。

## ⚠️ 注意事項

- **このリポジトリ内のHTMLファイルを直接編集しないでください。**
- すべての操作（生成、修正、承認、却下）は `copy-trade-core` リポジトリのスクリプトまたはダッシュボードの GitHub Actions を経由して行う必要があります。
- 直接編集を行うと、`core` リポジトリの管理データと不整合が発生し、デプロイフローが正常に動作しなくなる可能性があります。

## 詳細

運用の詳細や技術仕様については、`copy-trade-core/CLAUDE.md` を参照してください。