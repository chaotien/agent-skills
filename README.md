# agent-skills

A public monorepo of [Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) for Claude. | 給 Claude 用的公開 Agent Skills monorepo。

## Skills

| Skill | Description |
|---|---|
| [survey-mode](skills/survey-mode/SKILL.md) | Listen-and-digest mode for free writing / brain dumps: Claude only listens, marks key points, and surfaces tensions and gaps — no advice, no solutions — until you call stop, then it delivers an integrated digest board. |

## Installation | 安裝方式

### 1. Claude Code plugin marketplace

Add this repo as a marketplace, then install the skill as a plugin:

在 Claude Code 中把本 repo 加為 marketplace,再以 plugin 形式安裝:

```
/plugin marketplace add chaotien/agent-skills
/plugin install survey-mode@agent-skills
```

### 2. `npx skills add`

Install directly into your project with the [skills](https://github.com/vercel-labs/skills) CLI:

用 [skills](https://github.com/vercel-labs/skills) CLI 直接安裝到你的專案:

```
npx skills add chaotien/agent-skills
```

### 3. claude.ai — upload a `.skill` file | 上傳 `.skill` 檔

1. Download `survey-mode.skill` from the [latest release](https://github.com/chaotien/agent-skills/releases/latest).
   從 [latest release](https://github.com/chaotien/agent-skills/releases/latest) 下載 `survey-mode.skill`。
2. On [claude.ai](https://claude.ai), go to **Settings → Capabilities → Skills** and upload the file.
   在 [claude.ai](https://claude.ai) 開啟 **Settings → Capabilities → Skills**,上傳該檔案。
3. Enable the skill, then say "survey mode" in a conversation to trigger it.
   啟用後,在對話中說「survey mode」即可觸發。

## What is survey-mode? | survey-mode 是什麼?

When you want to free-write, brain-dump, or pour out context, the most valuable help isn't an answer — it's a listener that never interrupts, remembers everything, and sees the threads. In survey mode, Claude only **listens, digests, and marks key points**, and points out tensions and gaps. It gives zero advice and never converges until you say stop ("夠了", "停", "收斂") — then it hands you a structured digest board and gives the wheel back to you.

當你想 free writing、brain dump、倒垃圾式地輸出想法時,最有價值的協助不是「答案」,而是一個不搶話、記得住一切、看得出脈絡的聽眾。在 survey mode 裡,Claude 只**聽、消化、標記關鍵點**,指出張力與缺口,絕不給建議、不收斂——直到你喊停,才交出整合後的 digest board,並把方向盤還給你。

## License

[MIT](LICENSE)
