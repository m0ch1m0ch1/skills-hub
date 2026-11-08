# skills-hub

[gws-skills](https://github.com/m0ch1m0ch1/gws-skills) と [openshift-skills](https://github.com/m0ch1m0ch1/openshift-skills) の Claude Code スキルを、1 つのリポジトリから実行できるようにまとめたもの。

| スキル | 元のリポジトリ |
|---|---|
| gws-md2gdoc、gws-yaml2gsheet、gws-meeting-history、gws-gslides-translate-ja | gws-skills |
| openshift-runbook、openshift-must-gather-analysis、openshift-gws-doc-review、rhkcs-mcp-setup | openshift-skills |

## 使い方

```sh
git clone --recurse-submodules https://github.com/m0ch1m0ch1/skills-hub.git
cd skills-hub
claude
```

clone のときに `--recurse-submodules` を付け忘れたら、`git submodule update --init` を実行する。

スキルの入力・作業・結果 (`input/`、`.tmp/`、`runbooks/`、`must-gather-analyses/`、`gws-doc-reviews/`、`.rhkcs/`) は、このリポジトリのルートの下にでき、Git の管理対象外になる。

MCP サーバー (rhkcs、rhdocs) を使うときは、初回に Claude Code で承認するか、`.claude/settings.local.json` の `enabledMcpjsonServers` に足す。

## スキルを最新にする

```sh
git pull
git submodule update --init
```

## スキルを使うときの注意

Claude Code は `repos/` の下のスキルも見つけるので、同じスキルが `repos/<リポジトリ>:<skill>` という名前でも出てくる。こちらは使わず、`.claude/skills/` のもの (名前に `repos/…:` が付かないもの) を使う。`repos/` の下のスキルを使うと、入力・作業・結果がサブモジュールの中にでき、許可にも一致しない。

## 不具合・要望

スキルの不具合や要望は、元のリポジトリ ([gws-skills](https://github.com/m0ch1m0ch1/gws-skills/issues)、[openshift-skills](https://github.com/m0ch1m0ch1/openshift-skills/issues)) の Issue に書く。脆弱性は [SECURITY.md](SECURITY.md) を参照する。

## ライセンス

[MIT](LICENSE)。各スキルのライセンスは、元のリポジトリを参照する。
