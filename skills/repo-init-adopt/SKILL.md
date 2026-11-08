---
name: repo-init-adopt
description: 讓一個 repo 變成 agent-ready：新系統照固定形狀起 repo（init），既有 repo 盤點現況後補齊（adopt）——PLAN.md、CIP.md、AGENTS.md、docs/ 四件到位，讓任何 agent 和人都讀得懂、接得上。使用者說「開一個新 agent」「起 repo」「把這個 repo agent 化」「幫既有專案補 AGENTS.md」「讓 agent 接手這個系統」時，一律使用此 skill。
---

# Repo Init or Adopt（讓 repo 變成 agent-ready）

## 這個 skill 在解決什麼

agent 能不能接手一個系統，關鍵不在模型多聰明，而在 repo 裡有沒有它讀得懂的東西：這個系統要往哪走、現在走到哪、有哪些改進在排隊、做事的規矩是什麼。這些資訊平常散在人的腦袋、會議和聊天紀錄裡，agent 讀不到，換個人接手也讀不到。

所以這個 skill 只做一件事：**讓每個 repo 都長成同一個形狀**。形狀一致，任何 agent 和人一進來就知道該先讀哪裡；負責看全局的 manager agent，也能直接讀各個 repo 掌握戰況，不必靠口頭回報。

兩條路：

- **Init**：新系統，從零照形狀建。
- **Adopt**：既有系統，已經有 code 和文件，盤點後補齊缺的部分。實務上大部分會走這條。

它在開發流裡的位置：`survey-mode` → `rolling-plan` → **`repo-init-adopt`** → `cip-loop`。

## 固定形狀：四件

| 檔案 | 放什麼 | 誰維護 |
|---|---|---|
| `PLAN.md` | 終點、現況、phases、決策紀錄（見 `rolling-plan`） | owner＋agent |
| `CIP.md` | 持續改進項目（見 `cip-loop`） | 人和 agent 都可以記 |
| `AGENTS.md` | 給 agent 的操作守則 | owner |
| `docs/` | 背景、SOP、架構、owner 訪談收斂結果 | owner＋agent |

## AGENTS.md 最少要有這五段

```markdown
# AGENTS.md

## 1. 這個 agent 是誰
服務誰、負責哪個系統、終點是什麼（一句話，細節見 PLAN.md）。

## 2. 開工先讀
- PLAN.md 的「現況」與目前 phase
- CIP.md 裡 open / doing 的項目

## 3. 收工要做
- 這輪的發現記進 CIP.md，做完的改狀態
- 動到方向、phase 順序或完成條件的，在 PLAN.md 決策紀錄記一筆

## 4. 鐵律
（不能做的事。例如：不改某些目錄、不碰正式環境、敏感資料不進版控）

## 5. 背景去哪裡讀
（共用知識指到既有位置，不在這個 repo 另抄一份）
```

AGENTS.md 每一輪都會進 agent 的 context，所以**要短**。長的背景放 `docs/`，AGENTS.md 只寫去哪裡讀。

## Init 步驟（新 repo）

1. 用 `survey-mode` 跟 owner 倒出終點與需求。
2. 建四件：PLAN.md、CIP.md、AGENTS.md、docs/。
3. 交給 `rolling-plan` 寫第一個 phase。

## Adopt 步驟（既有 repo）

1. **盤點**：讀 code、README、既有文件，列出四件裡缺哪幾件、已有的寫到什麼程度。
2. **補背景**：只看 code 不夠時，用 `survey-mode` 問 owner；收斂結果寫進 `docs/`。第一版不用問得很完整，卡住的地方之後當 CIP 補。
3. **反推現況**：從 code、commit 和文件推出目前大概在哪個 phase，寫進 PLAN.md 的「現況」，並請 owner 確認。
4. **補齊缺的檔案。** 不搬動、不改寫既有的 code 與文件；既有文件可以從 AGENTS.md 或 docs/ 連過去。
5. 交給 `rolling-plan` 寫下一個 phase。

## 紅線

- **Adopt 時不重構。** 目標是讓 repo 讀得懂，不是讓它變漂亮。搬檔、改名、重寫既有文件，都要 owner 另外點頭。
- **不重抄共用知識。** 多個系統共用的背景（術語、平台說明、共通流程）指到它原本的位置。各 repo 各抄一份，很快就會各自過期。
- **不替 owner 編背景。** 查不到、問不到的，寫「待 owner 確認」，不推測。

## 完成檢查

- [ ] 四件都在
- [ ] AGENTS.md 五段都有寫，而且夠短
- [ ] PLAN.md 寫明現在在哪個 phase，owner 確認過
- [ ] 沒有重抄共用知識
- [ ] （Adopt）既有 code 與文件沒有被搬動或改寫
