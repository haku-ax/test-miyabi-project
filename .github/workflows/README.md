# GitHub Actions Workflows

このディレクトリには、Miyabiの自動化ワークフローが含まれています。

## 📋 有効なワークフロー

### 基本機能
- `autonomous-agent.yml` - AI Agentの自動実行
- `issue-opened.yml` - Issue作成時の自動処理
- `pr-opened.yml` - PR作成時の自動処理

### プロジェクト管理
- `auto-add-to-project.yml` - IssueをGitHub Projectsに自動追加
- `project-sync.yml` - プロジェクトステータス同期
- `state-machine.yml` - ステートマシン自動化
- `update-project-status.yml` - プロジェクトステータス更新

### CI/CD
- `deploy-pages.yml` - GitHub Pagesデプロイ
- `label-sync.yml` - ラベル同期

### レポート
- `weekly-kpi-report.yml` - 週次KPIレポート
- `weekly-report.yml` - 週次レポート

### セーフティ機能
- `economic-circuit-breaker.yml` - コスト制御（Circuit Breaker）

## ⚠️ 無効化されているワークフロー

### Webhook関連（2025-10-21に無効化）

以下のワークフローは、必要なスクリプトファイル（`scripts/webhook-router.ts`等）が
不足しているため、一時的に無効化されています。

- `webhook-event-router.yml.disabled` - Webhookイベントルーター
- `webhook-handler.yml.disabled` - Webhookイベントハンドラー

#### 🔄 再有効化の手順

必要なスクリプトファイルが揃ったら、以下の手順で再有効化してください：

```bash
# 1. 必要なスクリプトファイルを追加
#    - scripts/webhook-router.ts
#    - scripts/webhook-handler.ts (必要に応じて)

# 2. ワークフローファイルを元に戻す
mv .github/workflows/webhook-event-router.yml.disabled .github/workflows/webhook-event-router.yml
mv .github/workflows/webhook-handler.yml.disabled .github/workflows/webhook-handler.yml

# 3. 変更をコミット
git add .github/workflows/
git commit -m "feat: Re-enable webhook workflows"
git push
```

#### これらのワークフローの役割

**Webhook Event Router:**
- GitHubのWebhookイベント（push, PR, issue等）を受信
- イベントタイプに応じて適切な処理にルーティング
- 高度な自動化の基盤となる機能

**Webhook Handler:**
- Webhookイベントの実際の処理を実行
- カスタムロジックの実行
- 外部サービスとの連携

#### 無効化した理由

- `scripts/webhook-router.ts`ファイルが存在しない
- 実行のたびに失敗してメール通知が来る
- 基本的なAgent機能には影響しない

#### 将来的に必要になるケース

- 外部Webhookとの連携が必要な場合
- カスタム自動化ロジックを追加する場合
- より高度なイベント処理が必要な場合

---

## 📚 参考

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Miyabi Documentation](https://github.com/ShunsukeHayashi/Miyabi)
