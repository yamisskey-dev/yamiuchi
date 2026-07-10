<p align="center">
  <img src="yamiuchi.png" alt="yamiuchi" width="160">
</p>

# yamiuchi

[yamisskey-dev](https://github.com/yamisskey-dev) のメンバーを中心とした CTF チーム **yamiuchi** の writeup サイトです。

🔗 https://team.yami.ski/ （Cloudflare Pages: yamiuchi.pages.dev）

[MkDocs Material](https://squidfunk.github.io/mkdocs-material/) で構築。

## ローカルで動かす

```bash
uv sync
uv run mkdocs serve
# http://127.0.0.1:8000
```

## writeup を追加する

`docs/<年>/<CTF名>/` に Markdown を置くだけです。詳しくは
[writeup の書き方](docs/contributing.md) を参照。

main にマージすると Cloudflare Pages が自動でビルド・デプロイします。
PR を出すと**プレビュー URL** が自動生成されるので、マージ前に表示確認できます。

## デプロイ設定（初回のみ / Cloudflare Pages）

Cloudflare ダッシュボード → **Workers & Pages → Create → Pages → Connect to Git**
でこのリポジトリを連携し、以下を設定します。

| 項目 | 値 |
|---|---|
| Framework preset | None |
| Build command | `pip install -r requirements.txt && mkdocs build` |
| Build output directory | `site` |
| 環境変数 `PYTHON_VERSION` | `3.12` |

`requirements.txt` は `uv export` で生成済み（pin 済み）です。依存を変えたら
`uv export --frozen --no-hashes --no-dev -o requirements.txt` で更新してください。
