# Chatwork API ドキュメント

このリポジトリは、[Chatwork API](https://developer.chatwork.com/reference)の仕様に関するドキュメント情報を含んでいます。

## 概要

Chatwork APIは、Chatworkサービスの機能をプログラムから利用するためのREST APIです。メッセージの送受信、タスク管理、ファイル共有などの機能を外部アプリケーションから操作できます。

## API基本情報

- **ベースURL**: `https://api.chatwork.com/v2/`
- **認証方式**: APIトークンを使用したHTTPヘッダー認証
- **レスポンス形式**: JSON
- **API利用規約**: [Chatwork API 利用規約](https://developer.chatwork.com/ja/term.html)

## エンドポイント一覧

### 自分の情報

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/me` | GET | 自分の情報を取得する |
| `/my/status` | GET | 自分の状態を取得する |
| `/my/tasks` | GET | 自分のタスク一覧を取得する |

### コンタクト

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/contacts` | GET | コンタクト一覧を取得する |
| `/incoming_requests` | GET | コンタクト承認依頼一覧を取得する |
| `/incoming_requests/{request_id}` | PUT | コンタクト承認依頼を承認する |
| `/incoming_requests/{request_id}` | DELETE | コンタクト承認依頼を拒否する |

### チャット（ルーム）

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/rooms` | GET | チャット一覧を取得する |
| `/rooms` | POST | グループチャットを作成する |
| `/rooms/{room_id}` | GET | チャットの情報を取得する |
| `/rooms/{room_id}` | PUT | チャットの情報を変更する |
| `/rooms/{room_id}` | DELETE | チャットを退席/削除する |

### メンバー

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/rooms/{room_id}/members` | GET | チャットのメンバー一覧を取得する |
| `/rooms/{room_id}/members` | PUT | チャットのメンバーを変更する |

### メッセージ

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/rooms/{room_id}/messages` | GET | チャットのメッセージ一覧を取得する |
| `/rooms/{room_id}/messages` | POST | チャットにメッセージを投稿する |
| `/rooms/{room_id}/messages/read` | PUT | チャットのメッセージを既読にする |
| `/rooms/{room_id}/messages/unread` | PUT | チャットのメッセージを未読にする |
| `/rooms/{room_id}/messages/{message_id}` | GET | チャットのメッセージを取得する |
| `/rooms/{room_id}/messages/{message_id}` | PUT | チャットのメッセージを更新する |
| `/rooms/{room_id}/messages/{message_id}` | DELETE | チャットのメッセージを削除する |

### タスク

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/rooms/{room_id}/tasks` | GET | チャットのタスク一覧を取得する |
| `/rooms/{room_id}/tasks` | POST | チャットにタスクを追加する |
| `/rooms/{room_id}/tasks/{task_id}` | GET | チャットのタスクの情報を取得する |
| `/rooms/{room_id}/tasks/{task_id}/status` | PUT | チャットのタスクの完了状態を変更する |

### ファイル

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/rooms/{room_id}/files` | GET | チャットのファイル一覧を取得する |
| `/rooms/{room_id}/files` | POST | チャットにファイルをアップロードする |
| `/rooms/{room_id}/files/{file_id}` | GET | チャットのファイルの情報を取得する |

### 招待リンク

| エンドポイント | メソッド | 機能 |
|---|---|---|
| `/rooms/{room_id}/link` | GET | チャットへの招待リンクを取得する |
| `/rooms/{room_id}/link` | POST | チャットへの招待リンクを作成する |
| `/rooms/{room_id}/link` | PUT | チャットへの招待リンクを変更する |
| `/rooms/{room_id}/link` | DELETE | チャットへの招待リンクを削除する |

## レスポンスコード

### 成功レスポンス

- **200**: 成功（データあり）
- **204**: 成功（データなし）

### エラーレスポンス

- **400**: リクエストまたはアクセストークンのパラメーターが不足している、および不正な値が指定されている
- **401**: 認証に失敗した
- **403**: アクセストークンのスコープが不足している
- **404**: リソースが見つからない
- **429**: APIの利用回数制限を超過した

## レート制限

APIには利用回数制限があります。レスポンスヘッダーで以下の情報が返されます：

- `x-ratelimit-limit`: 一定期間におけるAPIの最大利用回数
- `x-ratelimit-remaining`: 一定期間におけるAPIの残り利用回数
- `x-ratelimit-reset`: API利用回数制限が次にリセットされる時間（Unix時間）

## 使用例

### 基本的なリクエスト（cURL）

```bash
curl --request GET \
  --url https://api.chatwork.com/v2/me \
  --header 'accept: application/json' \
  --header 'X-ChatWorkToken: YOUR_API_TOKEN'
```

### 対応言語

公式ドキュメントでは以下の言語でのサンプルコードが提供されています：

- Shell (cURL)
- Node.js
- Ruby
- PHP
- Python

## ファイル構成

- `llms.txt`: Chatwork APIドキュメント（https://developer.chatwork.com/reference）から抽出したテキスト情報
  - 抽出日時: 2025-06-25 16:12:01
  - 対象ページ数: 51ページ
  - 全APIエンドポイントの詳細情報を含む

## 参考リンク

- [Chatwork API 公式ドキュメント](https://developer.chatwork.com/reference)
- [Chatwork API 利用規約](https://developer.chatwork.com/ja/term.html)
- [Chatwork サービスサイト](https://go.chatwork.com/)

## ライセンス

本ドキュメントはChatwork株式会社の公式APIドキュメントから抽出された情報をまとめたものです。APIの利用については[Chatwork API 利用規約](https://developer.chatwork.com/ja/term.html)に従ってください。

---

*最終更新: 2025-06-25* 