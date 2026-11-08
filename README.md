# skills-hub

[gws-skills](https://github.com/m0ch1m0ch1/gws-skills) と [openshift-skills](https://github.com/m0ch1m0ch1/openshift-skills) の Claude Code 用のスキルを、1 つのリポジトリから使えるようにまとめたものです。スキルの中身は元のリポジトリにあり、ここではサブモジュールとして取り込んでいます。

## スキル

各スキルの前提条件・使い方・できあがるものの例は、スキル名のリンク先 (元のリポジトリの README) を参照してください。

### Google Workspace (gws-skills)

| スキル | できること |
| --- | --- |
| [gws-md2gdoc](https://github.com/m0ch1m0ch1/gws-skills/blob/main/.claude/skills/gws-md2gdoc/README.md) | Markdown (手順書など) を、見出しと番号付きの手順に組み直して、Google ドキュメントにする |
| [gws-yaml2gsheet](https://github.com/m0ch1m0ch1/gws-skills/blob/main/.claude/skills/gws-yaml2gsheet/README.md) | YAML (設定値や Kubernetes のマニフェストなど) を、Google スプレッドシートのパラメータシートにする |
| [gws-meeting-history](https://github.com/m0ch1m0ch1/gws-skills/blob/main/.claude/skills/gws-meeting-history/README.md) | 会議の名前から、その打ち合わせの経緯・課題と宿題・今後の予定を、カレンダーと直近の資料から要約する。何も作らない |
| [gws-gslides-translate-ja](https://github.com/m0ch1m0ch1/gws-skills/blob/main/.claude/skills/gws-gslides-translate-ja/README.md) | 既存の Google スライドをコピーして、文脈を踏まえた日本語版に作り直し、崩れたレイアウトを直す。元のスライドは変えない |

### OpenShift (openshift-skills)

| スキル | 使う場面 | できあがるもの |
| --- | --- | --- |
| [openshift-runbook](https://github.com/m0ch1m0ch1/openshift-skills/blob/main/.claude/skills/openshift-runbook/README.md) | 設定や構築の手順を作りたい | 接続中のクラスタで、適用・確認・切り戻しまで試した手順書 (`runbook.md`) |
| [openshift-must-gather-analysis](https://github.com/m0ch1m0ch1/openshift-skills/blob/main/.claude/skills/openshift-must-gather-analysis/README.md) | 起きた事象の原因を知りたい | must-gather から原因をさかのぼった、対処案付きの報告書 (`report.md`)。クラスタには接続しない |
| [openshift-gws-doc-review](https://github.com/m0ch1m0ch1/openshift-skills/blob/main/.claude/skills/openshift-gws-doc-review/README.md) | 資料 (Google ドキュメント・スライド) の技術的な内容を確かめたい | 誤りと懸念点を、場所・内容・根拠の表にまとめた Markdown |
| [rhkcs-mcp-setup](https://github.com/m0ch1m0ch1/openshift-skills/blob/main/.claude/skills/rhkcs-mcp-setup/README.md) | ほかのスキルから Red Hat のナレッジベースを読みたい | ナレッジベースを検索する MCP サーバー (rhkcs) の導入と設定 |

## 必要なもの

- gws-skills のスキル: [gws](https://github.com/googleworkspace/cli) (`gws auth login` で認証しておく)
- openshift-gws-doc-review: gws、[jq](https://jqlang.org/)
- openshift-runbook: `oc`
- openshift-must-gather-analysis: [omc](https://github.com/gmeghnag/omc)

細かい前提条件は各スキルの README を参照してください。足りないものがあれば、スキルが案内します。

## 使い始め方

1. サブモジュールごと clone して、ルートで Claude Code を起動します。

   ```sh
   git clone --recurse-submodules https://github.com/m0ch1m0ch1/skills-hub.git
   cd skills-hub
   claude
   ```

   `--recurse-submodules` を付け忘れたときは、`git submodule update --init` を実行します。

2. `/<スキル名>` でスキルを実行します (例: `/gws-md2gdoc`)。
3. ファイルを渡すスキル (gws-md2gdoc、gws-yaml2gsheet) では、ファイルを `input/<スキル名>/` に置いてから実行します。
4. 結果は `output/<スキル名>/` にできます (Git の管理対象外)。顧客やクラスタの情報を含むので、外に出すときは気をつけてください。

## Red Hat の情報源をつなぐ（任意）

OpenShift のスキルは、つなぐと Red Hat の公式ドキュメントとナレッジベースを直接読みます。つながなくても使えます。

| 情報源 | つなぎ方 |
| --- | --- |
| 公式ドキュメント (rhdocs) | `/mcp` で `rhdocs` を選び、Authenticate を選んで、Red Hat アカウントでログインする |
| ナレッジベース (rhkcs) | `/rhkcs-mcp-setup` を実行する |

初めて使うときは、Claude Code が MCP サーバーを使ってよいかを聞くので、承認してください。どちらも検索語が Red Hat に送られます (スキルは、クラスタ名などの固有の値を検索語に入れません)。

## スキルを最新にする

```sh
git pull
git submodule update --init
```

## 不具合・要望

スキルの不具合や要望は、元のリポジトリ ([gws-skills](https://github.com/m0ch1m0ch1/gws-skills/issues)、[openshift-skills](https://github.com/m0ch1m0ch1/openshift-skills/issues)) の Issue に書いてください。脆弱性の報告は [SECURITY.md](SECURITY.md) を参照してください。

## ライセンス

[MIT](LICENSE)。各スキルのライセンスは、元のリポジトリを参照してください。
