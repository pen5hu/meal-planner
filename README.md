# meal-planner

`meal-planner` は、登録済みの料理レパートリーと設定ルールに基づき、1週間分の夕食献立および買い物リストをAIエージェント（LLM）と連携して自動作成・管理するためのプロジェクトです。

---

## 📌 概要

毎週の献立決めや買い物リスト作成の手間を解消するため、以下の仕組みを提供します。

- **献立データの一元管理**: JSON形式で管理し、スキーマ定義によって整合性を担保
- **ルールベースの献立選定**: 重複防止、食材の使い回し、料理ジャンルのバランスを考慮
- **買い物リストの自動集計**: 献立に必要な食材を合算し、食材と調味料に分類してリスト化
- **AIタスク自動化**: GitHub上の最新データを取得し、定期実行（毎週金曜日午後）で献立と買い物リストを提案

---

## 📁 ディレクトリ・ファイル構成

```text
.
├── README.md                          # 本ドキュメント
├── meal.schema.json                   # メニューデータのJSONスキーマ定義
├── rules.json                         # 献立作成・買い物リスト集計のルール設定
├── meals/                             # 登録メニュー一覧のjsonを配置するディレクトリ（献立データ）
└── prompts/
    └── create-schedule-task.md        # 定期実行タスク用AIプロンプト定義
```

---

## 🚀 使い方

### 1. メニューを追加・編集する
[`meals/*.json`](file:///Users/shunpei/ghq/github.com/pen5hu/meal-planner/meals/*.json) にレパートリーを追加します。  
[`meal.schema.json`](file:///Users/shunpei/ghq/github.com/pen5hu/meal-planner/meal.schema.json) に準拠した形式で記述してください。

### 2. ルールを調整する
必要に応じて [`rules.json`](file:///Users/shunpei/ghq/github.com/pen5hu/meal-planner/rules.json) の設定値（計画日数や重複防止日数など）を変更します。

### 3. AIによる献立作成を実行する
[`prompts/create-schedule-task.md`](file:///Users/shunpei/ghq/github.com/pen5hu/meal-planner/prompts/create-schedule-task.md) を chatgpt 等の AI サービスのスケジュールタスク作成時に渡すプロンプト

AIがGitHubリポジトリ上の最新の [`meals/*.json`](file:///Users/shunpei/ghq/github.com/pen5hu/meal-planner/meals/*.json) および [`rules.json`](file:///Users/shunpei/ghq/github.com/pen5hu/meal-planner/rules.json) を取得し、以下のような形式で出力します。

1. **今週の献立**: 日付・曜日・メニュー名の一覧
2. **買い物リスト**: 食材および別枠の調味料リスト
