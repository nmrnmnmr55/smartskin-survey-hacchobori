# smartskin-survey-hacchobori（八丁堀院 顧客満足度アンケート）

神保町・横浜と同一設計の Streamlit アンケートアプリ。八丁堀院用。
全体設計・データフローは `../README_顧客満足度システム_全体設計.md` を参照。

## 院別差分（神保町/横浜との違いは2点のみ）
- 書込先ワークシート: `Hacchobori`（スプレッドシート `1R2QKVcLIwAwPE0b4GEr_f1fJ-4wNLt4ZDWyCGK8p-zo` 内の八丁堀タブ）
- Google口コミリンク: `REVIEW_URL`（`app_hacchobori.py` 冒頭。**八丁堀GBP公開後に確定・要差し替え**）

## デプロイ手順（Streamlit Cloud）
1. GitHubに `nmrnmnmr55/smartskin-survey-hacchobori` を作成し、本フォルダの内容を push（`app_hacchobori.py` / `requirements.txt` / `.gitignore`）。
2. Streamlit Cloud で当該リポジトリ・`app_hacchobori.py` を指定してデプロイ。
3. Streamlit Cloud の **Secrets** に、神保町/横浜と**同一の** `gcp_service_account`（サービスアカウントJSON）を登録。
   - スプレッドシートは共通のため、既存サービスアカウントに追加権限付与は不要（同一シートにアクセス権あり）。
4. 事前に スプレッドシートへ生データ用タブ `Hacchobori`（列A〜Fは既存院と同一）を作成しておく。
5. 発行URL `https://<app>.streamlit.app` を控え、MF来院後メッセージに `?d={システム管理用来院者ID}` を付けて差し込む。

## 前提・依存
- 八丁堀 MF API CLIENT_ID/SECRET（Enrichment側で使用・D4未発行）。
- 八丁堀GBPの口コミリンク（GBPオーナー確認/公開後）。
