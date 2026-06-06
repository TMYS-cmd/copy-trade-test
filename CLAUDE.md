# copy-trade-test リポジトリ ガイド

## このリポジトリの役割

Netlifyデプロイ専用のパブリックリポジトリ。
`copy-trade-core` で生成されたランディングページのステージング・承認・デプロイを管理する。

## 重要: このリポジトリのHTMLを直接編集しないこと

すべてのHTMLは `copy-trade-core` の `scripts/generate.sh` で生成される。
このリポジトリのHTMLを直接編集しても、次回の生成で上書きされる。

コンテンツを変更する場合は:
1. `copy-trade-core/content/landing-pages.yaml` を編集
2. `./scripts/generate.sh [page-id]` で再生成
3. `./scripts/sync-to-test.sh [slug]` でこのリポジトリに転送

## ディレクトリ説明

| ディレクトリ | 説明 | Netlify公開 |
|------------|------|------------|
| `_approved/` | 承認済みページ。Netlifyが公開するのはここのみ | **公開される** |
| `_staging/` | レビュー待ちページ | 公開されない |
| `_feedback/` | 却下フィードバックYAML | 公開されない |
| `pages/` | 全生成ページのアーカイブ | 公開されない |

## デプロイの仕組み

```
copy-trade-coreで: ./scripts/approve.sh [slug]
  → _approved/[slug]/index.html が作成される
  
このリポジトリで: git push
  → Netlifyが _approved/ のみを自動デプロイ
```

## 承認フロー

copy-trade-core のスクリプトを使って操作してください:

```bash
# copy-trade-core ディレクトリで実行
./scripts/approve.sh fx-copy-trade-beginner   # 承認
./scripts/reject.sh fx-copy-trade-beginner "理由"  # 却下
```

## Netlify設定の確認

`netlify.toml` の `publish = "_approved"` を**絶対に変更しないこと**。
この設定が承認制デプロイの唯一のメカニズム。

## 関連リポジトリ

- **copy-trade-core**: `C:\Users\kgtmy\Documents\copy-trade-core`（プライベート）
  - すべての操作はここから行う
