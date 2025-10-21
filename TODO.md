# TODO - test-miyabi-project

## 🔧 技術的な改善

### ワークフロー関連

- [ ] **Webhookワークフローの再有効化（将来）**
  - 優先度: 低
  - 作成日: 2025-10-21
  - 詳細:
    - 現在、以下のワークフローを無効化しています：
      - `webhook-event-router.yml.disabled`
      - `webhook-handler.yml.disabled`
    - **理由**: 必要なスクリプトファイル（`scripts/webhook-router.ts`）が不足
    - **再有効化の条件**:
      1. `scripts/webhook-router.ts`を実装
      2. `scripts/webhook-handler.ts`を実装（必要に応じて）
      3. `.disabled`拡張子を削除
    - **参考**: `.github/workflows/README.md`に詳細手順を記載

## 🎯 機能開発

- [ ] プロジェクトの基本機能を実装
- [ ] テストカバレッジを80%以上に

## 📝 メモ

- このプロジェクトは Miyabi v0.14.0-dev.0 で作成されました
- 基本的な7つのAIエージェントは正常に動作しています
