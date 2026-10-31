# 週間夕食献立・買い物リスト作成

GitHubリポジトリから最新のメニューデータおよびルールを取得し、`rules.json` の定義に従って次の1週間分の夕食献立と買い物リストを作成してください。

## データソース

- メニュー一覧：`https://raw.githubusercontent.com/pen5hu/meal-planner/main/meals/meals.json`
- ルール：`https://raw.githubusercontent.com/pen5hu/meal-planner/main/rules.json`

## 実行指示

1. 実行時点で上記URLから最新の `rules.json` および `meals.json` を取得してください。
2. 献立の対象期間・選定ルール・食材集計方針・出力形式などは、すべて `rules.json` の記述に厳密に従ってください。
3. データの取得に失敗した場合は推測で処理を行わず、その旨を報告して処理を中断してください。
