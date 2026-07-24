# CLAUDE.md

先讀 [AGENTS.md](./AGENTS.md) 了解專案的共用開發規則（指令、分支/commit 慣例、認證邊界等）。本檔案**只**補充 Claude Code 專屬設定，共用規則一律寫進 AGENTS.md，不要在此重複，避免兩份文件內容分裂。

## graphify

這個專案在 `graphify-out/` 有知識圖譜（god nodes、社群結構、跨檔案關係）。

規則：
- 問跟程式碼相關的問題時，先跑 `graphify query "<question>"`（`graphify-out/graph.json` 存在時）。用 `graphify path "<A>" "<B>"` 查關係，`graphify explain "<concept>"` 查特定概念。這些指令回傳的範圍較小的子圖，通常比讀 GRAPH_REPORT.md 或直接 grep 更有效率
- 若 `graphify-out/wiki/index.md` 存在，優先用它做整體導覽，而不是直接翻原始碼
- 只有在需要整體架構回顧、或 query/path/explain 查不到足夠內容時，才讀 `graphify-out/GRAPH_REPORT.md`
- 修改程式碼後執行 `graphify update .` 讓圖譜保持最新（僅 AST 分析，不耗費 API 額度）
