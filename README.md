# 100日100プロダクト 集約ページ

X（[いずみ｜AI導入支援](https://x.com/)）の100日チャレンジで作ったものを並べる公開ページ。
プロフィールの常設リンク先として使う。

## 中身は手で書かない

`index.html` は**生成物**。直接編集しても次の生成で上書きされる。
正本は開発ログ（`work/100days/logs/day-XXX-*.md`）で、そこから
`content-manifest.json` を経由してこのページが作られる。

```
daily-log（正本）
  → validate_daily_log.py
    → content-manifest.json
      → build_index_page.py
        → index.html + assets/
```

## 更新のしかた

Dayの検証が通ったあと、shiftai-elite-agents-main3 側で次を実行する。

```bash
python work/100days/scripts/build_index_page.py --out <このリポジトリのパス>
```

そのあと、このリポジトリで commit して push すれば公開に反映される。

- 掲載されるのは `ready_for_content_generation: true` のDayだけ
- 見出しは `problem`（解決した困りごと）。プロダクト名ではない
- 画像は `01-` プレフィックスのスクリーンショットを優先して自動コピーする

## 設定

文言・リンク・運営者表記は `build_index_page.py` 冒頭の設定ブロックで管理する。
このリポジトリ側では変更しない。

## 注意

- `.nojekyll` は Jekyll の処理を止めるために置いている。消さない
- 公開ページなので、掲載前に画像へ個人情報が写り込んでいないか必ず目視する
