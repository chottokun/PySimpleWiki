# PySimpleWiki

[SimpleWiki](https://github.com/chottokun/SimpleWiki)（PowerShell 製）の **Python 移植版**です。

移植するのは PowerShell コードの直訳ではなく、**OKF（Open Knowledge Format）v0.2 の読み方・並べ方・探し方と、機械可読 API（`/api/index.json`、`/api/chunks.json`）の考え方**です。Windows / PowerShell 固有の実装（WinRT 形態素解析、Markdig、DPAPI など）は、Python / Linux の部品へ置き換えます。

- 表示順の正本はファイル名ではなく各フォルダの `index.md` のリンク出現順
- 検索の重みは「一致した場所」（タイトル／タグ／概要／本文）につき、文書や話題の重要度にはつけない
- 検索コアは [pat-okf-agent](https://github.com/chottokun/pat-okf-agent) と共有する設計（当面は pat-okf-agent 側を正本とし、安定後に独立パッケージ化を判断）

## 状態

**足場のみ。** 実装はまだありません。現在は Python 3.12+、依存ゼロの最小構成です。HTTP サーバーと Markdown 描画のライブラリ方針は第1段の着手時に確定します。

## 段階計画

詳細は [docs/port-plan.md](docs/port-plan.md) を参照してください。

| 段 | 内容 |
|---|---|
| 第0段 | 互換性の物差し：本家の Pester テストとサンプルから、メタデータ・表示順・検索・API の受け入れフィクスチャを固定する |
| 第1段 | 核：読み取り専用サーバー。frontmatter 正規化、`index.md` 順の閲覧、検索、`/api/index.json` と `/api/chunks.json` |
| 第2段 | 静的 HTML エクスポート、メンテナンス点検、タグ同期（まず差分表示のみ） |
| 第3段 | エディタと履歴（作成・編集・保存・バックアップ・復元、読み取り専用モード） |
| 第4段 | RAG チャット（Fast / Agentic、OpenAI 互換 API・Ollama・LM Studio 接続） |
| 第5段 | 3D ステラ |

本家のアクティベーション（マシン指紋・DPAPI 前提の仕組み）は、知識機能ではないため Python 版の標準機能には含めません。

## ライセンス

MIT License — [LICENSE.md](LICENSE.md) を参照してください。本家 SimpleWiki と同じライセンスです。
