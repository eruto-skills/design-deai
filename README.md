# design-deai

> Claude Code skill — AI slop detector + DESIGN.md generator

AIコーディングツール（Claude Code・Cursor・v0・Lovable 等）が生成した UI コードの「AI 臭さ」をソースコード静的解析で診断し、脱スロップ化のための `DESIGN.md` を生成するスキル。

## What it does

1. **スロップパターン検出**: 紫グラデーション・Inter 固定・`rounded-2xl` 乱用・グラスモーフィズム・Empty/Error State 欠如・デザイントークン不在など 9 カテゴリを Grep で検出
2. **スロップスコア算出**: 0〜100 点で重症度を分類
3. **DESIGN.md 生成**: 検出されたアンチパターンを禁止事項として明記し、OKLCH カラーシステム・タイポグラフィ・スペーシング・コンポーネントルールを定義

## Installation

```
/plugin install design-deai@eruto-skills
```

## Usage

```
/design-deai [プロジェクトディレクトリパス]
```

引数省略時はカレントディレクトリを解析します。

## License

MIT
