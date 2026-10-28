# Orchestrator
指揮官工作流：Hermes 派工模板與可重用 profiles。

## 這是什麼

把 Hermes 當作 **主要模型**，負責拆任務、指派、追蹤；實際工作丟給
subagent / worker / external CLI（Claude Code、Codex、OpenClaude …）。

這個 repo 是那層「指揮官模式」的固定載體：
- 派工流程
- worker profile 範本
- 常見任務模板

## 結構

```
orchestrator/
├── README.md               ← 你在讀的這份
├── workflows/              ← 可重用任務模板
│   ├── feature.md
│   ├── review.md
│   └── research.md
└── profiles/               ← worker profile 範本
    ├── implementer.md
    ├── reviewer.md
    └── researcher.md
```

## 使用方式

1. 從 `workflows/` 選一個模板，或開新的
2. 從 `profiles/` 選 worker profile
3. 用 Hermes `delegate_task` 派出去

## 注意

- 這個 repo 是 Hermes 的**派工規則**，不是 worker 執行的環境
- worker 自己的 repo / worktree 由 kanban / project 機制管理

---

Created by Flint · 2026-10-29
