# agent-dev-flow 使用說明與範例流程

四支 skill 照順序用：`survey-mode` 倒料 → `rolling-plan` 排計畫 → `repo-init-adopt` 讓 repo 長成固定形狀 → `cip-loop` 邊用邊改，之後一直轉下去。新系統走 init，既有系統走 adopt。

## 什麼時候用哪一支

| 情境 | 用哪支 | 產出 |
|---|---|---|
| 想法還沒成形，要先把背景倒出來 | `survey-mode` | digest board |
| survey 收斂後、要開下一個 phase、方向有變 | `rolling-plan` | PLAN.md |
| 新系統要起 repo，或既有 repo 還沒有四件 | `repo-init-adopt` | PLAN.md、CIP.md、AGENTS.md、docs/，並推上遠端 |
| 用了、測了發現想改的；開工要挑工作 | `cip-loop` | CIP.md 一行一項 |

## 範例一：新系統（init）

情境：要做一個「每週報表自動整理」的 agent，目前什麼都沒有。

1. **Survey**：對 agent 說「survey mode」，自由講：誰在用報表、現在怎麼做、最痛的是哪一步、資料在哪。講完說「收斂」，拿到 digest board。
2. **Plan**：說「照 digest 寫 PLAN.md」。agent 會寫終點（例：每週一早上報表已經在共用資料夾，負責人只需檢查）、Phase 1 寫細、Phase 2 以後只寫方向，不寫日期。
3. **Init repo**：說「照固定形狀起 repo」。agent 建 PLAN.md、CIP.md、AGENTS.md、docs/，把 survey 的背景放進 docs/，再**建立遠端 remote（例如 GitLab）並推上第一個 commit**。
4. **開始做 Phase 1**：每次開工說「開工」，agent 先讀 PLAN.md 現況和 CIP.md 的 open 項目，挑一項做。
5. **CIP**：用的過程中想到「欄位順序要改」，直接說「記一條 CIP」，agent 寫一行，不當場爭論要不要做。
6. **Phase 結束**：完成條件達成後，先對 Phase 2 做一輪 survey，再用 rolling-plan 把 Phase 2 寫細。

## 範例二：既有系統（adopt）

情境：一個已經上線的系統，有 code、有 README，但沒有 PLAN.md、CIP.md、AGENTS.md。

1. **盤點**：說「adopt 這個 repo」。agent 讀 code、README、既有文件，列出四件缺哪幾件，也確認有沒有遠端 remote。
2. **補背景**：agent 列出看 code 看不出來的問題，owner 用 survey mode 回答，收斂結果寫進 docs/。第一版不求完整。
3. **反推現況**：agent 從 code 和 commit 推出現在大概在哪個 phase，寫進 PLAN.md 現況，owner 確認。
4. **補齊**：補上缺的檔案，不搬動、不改寫既有 code 與文件。
5. **推上遠端**：還沒有 remote 的，建一個並推上去；已經有的，把補齊的檔案 commit、push。
6. **寫下一個 phase**：交給 rolling-plan，把接下來要做的寫細。
7. **進入 CIP 迴圈**：之後跟範例一的第 4、5 步一樣。

## 每天的節奏

| 時機 | 對 agent 說 | agent 做什麼 |
|---|---|---|
| 開工 | 「開工」 | 讀 PLAN.md 現況與 CIP.md，建議挑哪一項 |
| 做事中 | 「記一條 CIP：…」 | CIP.md 加一行 |
| 收工 | 「收工」 | 更新 CIP 狀態；動到方向的回寫 PLAN.md 決策紀錄；commit、push |
| 方向有變 | 「更新 plan」 | 用 rolling-plan 改 PLAN.md，記決策紀錄 |

## 常見問題

- **CIP 和 PLAN 怎麼分？** 小改進只進 CIP.md；動到方向、phase 順序或完成條件的，才在 PLAN.md 決策紀錄記一筆並連回那條 CIP。
- **遠的 phase 寫不出來怎麼辦？** 正常。只寫一兩句方向，等前一個 phase 做完再 survey、再寫細。
- **共用知識要不要抄進每個 repo？** 不要。AGENTS.md 只寫去哪裡讀。
- **為什麼一定要有遠端 remote？** 只在自己筆電上的 repo，別人和 manager agent 都讀不到，也沒有備份。
- **skill 本身不好用怎麼辦？** 記進 agent-skills repo 的 CIP.md，這套開發流也會照同樣方式進化。
