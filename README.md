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

## Codex / Claude Code installation

This package supports both Codex and Claude Code. The plugin entry point is
`skills/design-deai/SKILL.md`; the root `SKILL.md` remains the standalone source.

For Codex, add the public `eruto-skills` marketplace in the plugin UI using
`https://github.com/eruto-skills/marketplace`, then install `design-deai`.
To install as a standalone user skill instead:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/eruto-skills/design-deai.git ~/.agents/skills/design-deai
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE/.agents/skills" | Out-Null
git clone https://github.com/eruto-skills/design-deai.git "$env:USERPROFILE/.agents/skills/design-deai"
```

In Codex, select the installed skill by name or invoke `$design-deai` with a task.
In Claude Code:

```text
/plugin marketplace add eruto-skills/marketplace
/plugin install design-deai@eruto-skills
```

The instructions use the tools available in the current host. Scripts are resolved
from the actual skill directory, rather than a fixed author path. Additional browser,
Python, or format-specific dependencies are described in `SKILL.md` and the references;
installing the plugin alone does not install those external programs.

## Maintaining the plugin package

Edit the root `SKILL.md` and its supporting resources, then run:

```bash
node scripts/package-plugin.mjs
node scripts/package-plugin.mjs --check
```

Commit the generated `skills/` files with the source changes. CI checks that both
layouts match, including the Claude manifest. Do not edit generated files directly.
