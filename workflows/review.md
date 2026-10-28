# Review Workflow

## 觸發

- implementer 完成後進入 review
- 安全關鍵、核心流程、重大改動的強制步驟

## 步驟

1. implementer 完成後 `kanban_request_review`
2. 指揮官指派 `reviewer`
3. `reviewer` 審查 artifact / diff：
   - approve → `kanban_complete`
   - request_changes → `kanban_request_changes`，回到 implementer
4. implementer 修正後重送 review
5. 重複 2-4 最多 2 次，超過就 escalation

## 檢查點

- [ ] reviewer 的意見具體到可以直接改
- [ ] implementer 有實際跑過測試 / 手動驗證
- [ ] 沒有 "隨便過" 的 review
- [ ] 最多 2 輪 review，超過 escalation

## 注意

- reviewer 只看證據，不要猜實作動機
- 指令稿 / 安規 / 隱私相關的改动，review 要額外嚴格
- 小改動（ typo、註解、config）可以指揮官直接 approve，不用走 formal review
