# copy-trade-test リポジトリ ガイド

## このリポジトリの役割

Netlifyデプロイ専用のパブリックリポジトリ。
`copy-trade-core` で生成されたランディングページの承認・デプロイを管理する。

## 重要: このリポジトリのHTMLを直接編集しないこと

すべてのHTMLは `copy-trade-core` の Claude Code 経由で生成される。
このリポジトリのHTMLを直接編集しても、次回の生成で上書きされる。

コンテンツを変更する場合は:
1. `copy-trade-core/content/landing-pages.yaml` を編集してコミット
2. Claude Code に HTML 生成を依頼
3. `bash scripts/post-generate.sh [page-id]` で後処理

## ディレクトリ説明

| ディレクトリ | 説明 | Netlify公開 |
|------------|------|------------|
| `_approved/` | 承認済みページ。Netlifyが公開するのはここのみ | **公開される** |
| `pages/` | 生成済み HTML のアーカイブ（レビュー・承認待ち） | 公開されない |
| `docs/` | ダッシュボード（GitHub Pages） | GitHub Pages で公開 |

## デプロイの仕組み

```
copy-trade-core で: bash scripts/post-generate.sh [page-id]
  → pages/[slug]/index.html が作成・コミットされる

ダッシュボードで「✅ 承認」ボタン
  → GitHub Actions approve-page.yml が実行される
  → _approved/[slug]/index.html がコピーされる

このリポジトリで: git push（Actions が自動実行）
  → Netlifyが _approved/ のみを自動デプロイ
```

## Netlify設定の確認

`netlify.toml` の `publish = "_approved"` を**絶対に変更しないこと**。
この設定が承認制デプロイの唯一のメカニズム。

## 関連リポジトリ

- **copy-trade-core**: `C:\Users\kgtmy\Documents\copy-trade-core`（プライベート）
  - すべての操作はここから行う
  - 詳細は `copy-trade-core/docs/GUIDE.md` を参照
