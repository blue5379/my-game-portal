# GitHub Pages 公開手順

ドメイン取得元: お名前ドットコム
ドメイン: stormphilia.com
リポジトリ: https://github.com/blue5379/my-game-portal

---

## STEP 1 — コードを GitHub に push する

```bash
git add .
git commit -m "Prepare for GitHub Pages"
git push origin main
```

---

## STEP 2 — リポジトリを Public にする

1. `https://github.com/blue5379/my-game-portal` を開く
2. `Settings` → 一番下 **Danger Zone**
3. `Change repository visibility` → `Change to public`

---

## STEP 3 — GitHub Pages を有効化する

1. `Settings` → 左メニュー `Pages`
2. **Source** を `Deploy from a branch` に設定
3. **Branch** を `main` / `/ (root)` に設定して `Save`

確認 URL: `https://blue5379.github.io/my-game-portal/`

---

## STEP 4 — お名前ドットコムのネームサーバーを変更する

DNS レコードを編集するため、ネームサーバーを以下に変更する。

```
01.dnsv.jp
02.dnsv.jp
03.dnsv.jp
04.dnsv.jp
```

> 反映まで最大72時間かかる場合がある。

---

## STEP 5 — お名前ドットコムで DNS レコードを設定する

管理画面: `ドメイン管理` → 対象ドメイン → `DNS設定` → `DNSレコード設定`

### A レコード（4つ）

| ホスト名 | タイプ | 値 | TTL |
|---|---|---|---|
| @ | A | 185.199.108.153 | 300 |
| @ | A | 185.199.109.153 | 300 |
| @ | A | 185.199.110.153 | 300 |
| @ | A | 185.199.111.153 | 300 |

### CNAME レコード

| ホスト名 | タイプ | 値 | TTL |
|---|---|---|---|
| www | CNAME | blue5379.github.io | 300 |

> 反映まで数時間かかる場合がある。

---

## STEP 6 — GitHub Pages にカスタムドメインを設定する

1. `Settings` → `Pages`
2. **Custom domain** に `stormphilia.com` を入力して `Save`
3. DNS 反映後、**Enforce HTTPS** にチェックを入れる

---

## STEP 7 — CNAME ファイルを追加する

```bash
echo "stormphilia.com" > CNAME
git add CNAME
git commit -m "Add CNAME for custom domain stormphilia.com"
git push origin main
```

> GitHub Pages 側で自動生成された場合は `git pull --rebase origin main` してから push する。

---

## サイト更新手順

```bash
git add .
git commit -m "Update"
git push origin main
```

push 後、数分以内に `https://stormphilia.com` に反映される。
