# gap-scan

[English](../../README.md) · [简体中文](./README_zh-CN.md) · **日本語** · [한국어](./README_ko.md) · [Español](./README_es.md) · [Deutsch](./README_de.md) · [Português (Brasil)](./README_pt-BR.md)

スタートアップのギャップが「本物の会社」なのか「大手に取り込まれる Feature」なのかを分けるポータブルなプロンプトスキルです。Claude Code、Cursor、Codex CLI、GitHub Copilot、Antigravity、system prompt を受け付けるあらゆる LLM で動作します。

## 問題

ほとんどの LLM「スタートアップアイデア評価器」はあなたのアイデアが素晴らしいと言います。反対するものは一般的な PESTEL 分析を渡します。どちらも本当に重要な 2 つの質問に答えません。

**質問 1（Barred テスト）：** 最適な位置にいるインカンバントは、構造的にこれを作れない状態か？ OpenAI、Cursor、Google、Microsoft が週末 Feature として出せるなら、あなたは会社を持っていません。吸収待ちの Feature を持っています。

**質問 2（Reach テスト）：** 最初の 10-20 ユーザーは、今日到達可能な名前のある人間ですか？ フルネームとチャネルで列挙できないなら、あなたは市場を持っていません。仮説を持っています。

どちらかが失敗すれば、TAM スライドが何を主張しようと、そのアイデアは会社ではありません。

## 機能

gap-scan は並列エビデンス脚で両方のテストを実行し、3 つの判定のいずれかを出力します：

- **COMPANY**：両方合格。最初の 10 ユーザーリスト、Barred 論拠、あなたを守る構造的コンフリクトを提供。
- **FEATURE**：Barred テスト失敗。吸収しそうなインカンバントとタイムラインを名指し。
- **HYPOTHESIS**：Reach テスト失敗。研究ギャップを特定：会社になる前に誰にインタビューする必要があるか。

## インストール

### Claude Code

```bash
git clone https://github.com/LuciferDono/gap-scan ~/.claude/skills/gap-scan
```

### Cursor

```bash
mkdir -p .cursor/rules && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/cursor/gap-scan.mdc -o .cursor/rules/gap-scan.mdc
```

他のエージェントは [`dist/`](../../dist/) を参照。

## トリガーフレーズ

"is this a company or a feature?", "untapped market", "should I build this?", "why isn't this just a Cursor feature?", "/gap-scan"。

## License

MIT。[LICENSE](../../LICENSE)。
