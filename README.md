# agent-skills

A public monorepo of [Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) for Claude. | 給 Claude 用的公開 Agent Skills monorepo。

## Skills

| Skill | Description |
|---|---|
| [survey-mode](skills/survey-mode/SKILL.md) | Listen-and-digest mode for free writing / brain dumps: Claude only listens, marks key points, and surfaces tensions and gaps — no advice, no solutions — until you call stop, then it delivers an integrated digest board. |
| [swiss-slide-style](skills/swiss-slide-style/SKILL.md) | Swiss-minimal slide spec for upward-reporting decks: red `#C00000` = what needs attention, blue `#1912F7` = fixes and results, line style = status; large-type exec variant, Gantt rules, and wording rules. |

## Installation | 安裝方式

### 1. Claude Code plugin marketplace

Add this repo as a marketplace, then install the skill as a plugin:

在 Claude Code 中把本 repo 加為 marketplace,再以 plugin 形式安裝:

```
/plugin marketplace add chaotien/agent-skills
/plugin install survey-mode@agent-skills
/plugin install swiss-slide-style@agent-skills
```

### 2. `npx skills add`

Install directly into your project with the [skills](https://github.com/vercel-labs/skills) CLI:

用 [skills](https://github.com/vercel-labs/skills) CLI 直接安裝到你的專案:

```
npx skills add chaotien/agent-skills
```

### 3. claude.ai — upload a `.skill` file | 上傳 `.skill` 檔

1. Download `survey-mode.skill` or `swiss-slide-style.skill` from the [latest release](https://github.com/chaotien/agent-skills/releases/latest).
   從 [latest release](https://github.com/chaotien/agent-skills/releases/latest) 下載 `survey-mode.skill` 或 `swiss-slide-style.skill`。
2. On [claude.ai](https://claude.ai), go to **Settings → Capabilities → Skills** and upload the file.
   在 [claude.ai](https://claude.ai) 開啟 **Settings → Capabilities → Skills**,上傳該檔案。
3. Enable the skill, then say "survey mode" in a conversation to trigger it.
   啟用後,在對話中說「survey mode」即可觸發。

### 4. Any other agent — plain `SKILL.md` | 其他 agent:直接下載 `SKILL.md`

Each skill is a single Markdown file, so any agent that reads a skills folder (OpenCode, Codex, a custom harness) can use it as-is:

每個 skill 都是單一 Markdown 檔,任何會讀 skills 資料夾的 agent(OpenCode、Codex、自建 harness)都能直接用:

```
mkdir -p .agents/skills/swiss-slide-style
curl -L -o .agents/skills/swiss-slide-style/SKILL.md \
  https://raw.githubusercontent.com/chaotien/agent-skills/main/skills/swiss-slide-style/SKILL.md
```

Change the target folder to whatever your agent reads (e.g. `.claude/skills/`, `.opencode/skills/`). If the agent has no skills support, paste the file into its system prompt or `AGENTS.md`.

目標資料夾改成你的 agent 會讀的位置(例如 `.claude/skills/`、`.opencode/skills/`)。不支援 skills 的 agent,把檔案內容貼進 system prompt 或 `AGENTS.md` 即可。

## What is survey-mode? | survey-mode 是什麼?

When you want to free-write, brain-dump, or pour out context, the most valuable help isn't an answer — it's a listener that never interrupts, remembers everything, and sees the threads. In survey mode, Claude only **listens, digests, and marks key points**, and points out tensions and gaps. It gives zero advice and never converges until you say stop ("夠了", "停", "收斂") — then it hands you a structured digest board, and you decide what's next: converge, start planning, or keep dumping.

當你想 free writing、brain dump、倒垃圾式地輸出想法時,最有價值的協助不是「答案」,而是一個不搶話、記得住一切、看得出脈絡的聽眾。在 survey mode 裡,Claude 只**聽、消化、標記關鍵點**,指出張力與缺口,絕不給建議、不收斂——直到你喊停,才交出整合後的 digest board,由你決定下一步——收斂、想方案,或再補一輪。

## What is swiss-slide-style? | swiss-slide-style 是什麼?

A slide spec for decks that report upward: one idea per slide, large type, and **one meaning per color**. Red marks what needs attention (pain points, gaps, risk, deadlines); blue marks the fix and the result (actions, milestones, shipped, positive numbers). Line style carries status independently — solid = done, outline = in progress, dashed = not yet. It also covers a large-type variant for execs, Gantt conventions (min/max ranges, holidays, milestones), wording rules ("write what it achieves, not what we do"), speaker notes, and HTML→PPT export pitfalls.

給向上報告用的投影片規格:一頁一件事、字要大、**一個顏色只代表一個意思**。紅色標要注意的事(痛點、缺口、風險、deadline),藍色標解法與成果(動作、里程碑、已上線、正面數字);線型獨立表示狀態——實心＝完成、空心＝進行中、虛線＝還沒有。另含長官版大字級、Gantt 慣例(上下限區間、假日、里程碑)、用字規則(寫「做完會怎樣」而不是「我們怎麼做」)、講稿,以及 HTML 匯出 PPT 的注意事項。

## License

[MIT](LICENSE)
