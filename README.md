# Holiday Flight Planner｜連假彈性機票規劃

將官方連假研究、彈性日期比價、請假成本、去回程航班核對與旅遊報告製作整合成可重複使用的 Agent Skill。

## 安裝

需先具備 Node.js 與 npm／npx。使用 [Skills CLI](https://github.com/vercel-labs/skills) 安裝到 Codex：

```sh
npx skills add lyhcode/holiday-flight-planner --skill holiday-flight-planner -g -a codex
```

若要互動選擇其他支援的 agent：

```sh
npx skills add lyhcode/holiday-flight-planner
```

也可下載 repository ZIP，將包含 `SKILL.md`、`agents/`、`references/` 的資料夾命名為 `holiday-flight-planner`，放進 Codex 技能目錄 `~/.codex/skills/`。若設定了 `CODEX_HOME`，使用其下的 `skills/`。請避免將同一技能重複安裝到多個位置。

## 使用範例

```text
使用 $holiday-flight-planner，找 2027 年上半年台灣連假，
台北飛大阪玩 4～5 天，去回日期可各前後調整 3 天，
最多請假 2 天，最後做成 PDF 報告。
```

其他情境：

- 「幫我比較清明連假附近的機票，要含托運行李。」
- 「最多只請一天假，幫我重排剛才的方案。」
- 「加一點預算能不能晚一點回來，多玩半天？」
- 「把剛才的查詢結果做成可分享的報告。」

## 工作流程

1. 確認路線、旅行期間、人數、天數、工作週與日期彈性。
2. 查核官方假日與補假，區分自然連假及自行請假串接。
3. 比較連假附近的日期組合，計算請假及同天數基準的票價差。
4. 核對主要方案的去回程、機場、當地時間、轉機與分段購票。
5. 提出最低價、少請假、较好航班時間等有價值的方案。
6. 依需求製作包含查詢日期、證據層級與來源連結的報告。

預設 4～5 天、日期各前後 1～3 天、1 成人經濟艙、優先直飛；使用者可調整。目的地、年份、幣別與假日管轄區不限台灣或日本。

## 環境需求與範圍

這是給 AI agent 的流程指引，不是獨立爬蟲或訂票程式。使用端需提供網路研究及可用的瀏覽器操作工具；Google 機票互動操作可依環境使用 agent-browser 或其他瀏覽器工具。製作 PDF 另需可用的文件工具與中文字體，相關工具不隨此套件安裝。

技能會區分日期網格估價、已核對去回程及已查看出票頁，並標示資料時間。它不自動購票、付款或設定價格監控。

## 檔案

- [SKILL.md](SKILL.md)：技能入口與主要規劃流程。
- [Google 機票操作指引](references/google-flights.md)：載入狀態、日期核對及證據紀錄。
- [報告指引](references/report.md)：報告結構與品質檢查。
- [Codex 顯示資訊](agents/openai.yaml)：技能名稱與呼叫範例。
