# Feature Workflow

## 觸發

- 新功能開發
- 重大改動
- 需要多步驟實作的任務

## 步驟

1. **指揮官** 讀 task body，確認清楚後開 kanban card
2. 指派 `researcher`（若需要技術選型）
3. 指派 `implementer` 實作
4. `implementer` 完成後 `kanban_request_review`
5. 指派 `reviewer` review
6. review 通過 → `kanban_complete`
7. review 不通過 → `kanban_request_changes`，回到 step 3

## 檢查點

- [ ] task body 有驗收條件
- [ ] implementer 有跑測試 / 手動驗證
- [ ] reviewer 留下具體意見
- [ ] 合併前沒有未解決的 blocker

## 注意

- 每一步都留在 kanban card 的 comment / event
- 不要跳過 review；除非 task body 明確寫明可跳
