# cli-kintone ドキュメント統合コンテンツ

このファイル(`llms.txt`)は、cli-kintone の公式ドキュメントから抽出された統合コンテンツです。

## 概要

- **抽出日時**: 2025-08-04 16:49:23
- **総ページ数**: 33ページ
- **対象サイト**: https://cli.kintone.dev/
- **用途**: NotebookLM用の統合リファレンス

## 含まれる内容

### 1. レコードのエクスポート（Exporting records）
- CSV形式でのレコードエクスポート機能
- 区切り文字（デリミタ）の設定
- 文字エンコーディング（UTF-8, Shift-JIS）
- フィールド指定とソート
- 添付ファイルの取り扱い
- テーブルフィールドの処理
- ユーザー・グループ・部署選択フィールド

### 2. レコードのインポート（Importing records）
- CSV形式でのレコードインポート機能
- UPSERT機能（更新または挿入）
- 文字エンコーディングの指定
- エラーハンドリング
- 添付ファイルのアップロード
- テーブルフィールドの処理

### 3. レコードの削除（Deleting records）
- 全レコードの削除
- 指定レコードの削除
- APIトークンによる認証
- 確認プロンプト機能

### 4. エラーハンドリング
- 文字エンコーディングの不一致
- ネットワークタイムアウト
- APIリクエストのリトライ機能

### 5. プロキシ設定
- HTTPプロキシの使用
- プロキシ認証（Basic認証）

### 6. ログ機能
- ログレベルの設定
- 詳細ログ（verbose）モード
- ログフォーマット

## 主要な機能

### エクスポート
```bash
# 基本的なエクスポート
cli-kintone record export --app 8

# 文字エンコーディング指定
cli-kintone record export --app 8 --encoding sjis

# フィールド指定
cli-kintone record export --app 8 --fields 'Number,Text'

# 添付ファイル付きエクスポート
cli-kintone record export --app 8 --attachment-dir ./attachments
```

### インポート
```bash
# 基本的なインポート
cli-kintone record import --app 8 --file-path records.csv

# UPSERT（更新または挿入）
cli-kintone record import --app 8 --file-path records.csv --update-key companyName

# 添付ファイル付きインポート
cli-kintone record import --app 8 --file-path records.csv --attachment-dir ./attachments
```

### 削除
```bash
# 全レコード削除
cli-kintone record delete --app 8

# 指定レコード削除
cli-kintone record delete --app 8 --file-path records.csv

# 確認なしで実行
cli-kintone record delete --app 8 --yes
```

## サポートされるフィールドタイプ

- テキスト（1行、複数行、リッチテキスト）
- 数値、計算フィールド
- チェックボックス、ラジオボタン、ドロップダウン
- ユーザー・グループ・部署選択
- 日付、時刻、日時
- リンク、添付ファイル
- テーブル

## 注意事項

- **認証**: レコード削除機能はAPIトークンのみサポート
- **文字エンコーディング**: UTF-8、Shift-JISをサポート
- **添付ファイル**: 1GB以下のファイルサイズ制限
- **タイムアウト**: デフォルト600秒のネットワークタイムアウト

## 関連リンク

- [公式ドキュメント](https://cli.kintone.dev/)
- [リファレンス](https://cli.kintone.dev/reference/)
- [ガイド](https://cli.kintone.dev/guide/)

---

このドキュメントは、cli-kintone の包括的な機能を理解するためのリファレンスとして使用してください。