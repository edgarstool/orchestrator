# Orchestrator

指揮官工作流：Hermes 做派工中枢，背景程式都是 worker。

## 架構

```
語音/文字輸入
    ↓
Hermes（指揮官）— 拆任務、派工、整合、回覆
    ↓
┌──────────┬──────────┬──────────┐
│ worker A │ worker B │ worker C │  ← delegate_task
│ (研究)   │ (實作)   │ (review) │
└──────────┴──────────┴──────────┘
```

指揮官 **不做細節實作**，只做：
- 任務分解
- worker 選型與派發
- 結果整合
- 對使用者回覆

## 目錄

```
orchestrator/
├── README.md                    ← 你在讀的這份
├── profiles/                    ← 角色定義
│   ├── orchestrator.md          ← 指揮官（主要模型）
│   ├── worker.md                ← 背景程式通用規範
│   ├── researcher.md            ← 研究型工人
│   ├── implementer.md           ← 實作型工人
│   └── reviewer.md              ← 審查型工人
├── workflows/                   ← 可重用流程
│   ├── feature.md               ← 新功能開發
│   ├── research.md              ← 資料研究
│   └── review.md                ← 審查流程
└── templates/                   ← task body 範本
    ├── feature-task.md
    ├── research-task.md
    └── bugfix-task.md
```

## 使用方式

1. 收到需求後，指揮官先判斷屬於哪條 workflow
2. 從 `templates/` 選一個 task template 填寫
3. 開 kanban card，指派對應 profile
4. 用 `delegate_task` 派出去，`context` 寫清楚
5. worker 回傳後，指揮官 judge 結果
6. 需要就補派 / 重派；足夠就整合回覆

## 派工原則

- 同層並行不超過 8 個 worker
- 單一 `goal` 要小到 1-2 輪能做完；做不到就再拆
- 有相依性的任務用 kanban parent/child 串起來
- worker 回傳 findings 時，指揮官要 judge 夠不夠，不夠就補派

## 注意

- 這個 repo 是**派工規則的載體**，不是 worker 執行的環境
- worker 的 execution environment 由各自的 task / worktree 管理
- 每次有新 workflow 或 worker profile，先寫進來再派

---

Created by Flint · 2026-10-29
