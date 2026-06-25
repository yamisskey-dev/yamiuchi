# writeup の書き方

writeup は `docs/` 配下に **Markdown ファイルを置くだけ** で公開されます。
ナビゲーションは自動生成されるので、`mkdocs.yml` を編集する必要はありません。

## ディレクトリ構成

```
docs/
  <年>/
    <CTF名>/
      index.md        # その CTF の概要（順位・得点・問題一覧）
      <カテゴリ>-<問題名>.md   # 各問題の writeup
```

例: `docs/2026/SECCON/web-sample.md`

ファイル名は `web-login`, `pwn-bof`, `crypto-rsa` のように
**`カテゴリ-問題名`** にすると一覧で分かりやすいです。

## 新しい writeup を追加する手順

1. `docs/2026/SECCON/` のように `年/CTF名/` フォルダを作る（無ければ）
2. `index.md` に概要を書く（[テンプレ](2026/SECCON/index.md)をコピー）
3. 問題ごとに `.md` を作る（[サンプル](2026/SECCON/web-sample.md)をコピー）
4. ファイル冒頭の `tags:` にカテゴリ等を書くと [タグ一覧](tags.md) に載る
5. PR を出す → main にマージされると自動デプロイ

## ローカルでプレビュー

```bash
uv sync           # 初回のみ
uv run mkdocs serve
# http://127.0.0.1:8000 を開く
```

## 便利な記法

### flag を隠す（spoiler）

```markdown
??? success "Flag を表示"
    SECCON{...}
```

### 注記ボックス

```markdown
!!! info "問題情報"
    カテゴリ: web / 配点: 100pts
!!! warning "ハマりどころ"
    ...
```

### 数式（crypto 向け）

`$ ... $` でインライン、`$$ ... $$` でブロック。KaTeX でレンダリングされます。

### コードハイライト

````markdown
```python
print("hello")
```
````
