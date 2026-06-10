# 株式会社イシヤマ LP — HTML/CSS

モバイルファースト（SP 375基準）でビルド中。
WordPress 固定ページ貼付け＋Contact Form 7 連携を想定。

---

## ディレクトリ構成

```
ishiyama-lp/
├── index.html      ← 全セクション セマンティックHTML
├── css/style.css   ← 1ファイル（モバイルファースト）
├── images/         ← 後で差し替え（下記参照）
└── README.md       ← この資料
```

---

## 必要な画像アセット

`images/` 配下に下記ファイル名で配置してください（差替え後リネーム不要）。

| ファイル | 用途 | 推奨サイズ |
|---|---|---|
| `hero-door.jpg` | ヒーロー写真（人物＋玄関ドア） | 750×860px〜 |
| `case-01.jpg` | 施工事例 1（マンション外観など） | 670×360px |
| `case-02.jpg` | 施工事例 2 | 670×360px |
| `youtube-thumb-01.jpg` *任意* | 動画サムネ前半 | 670×378px |
| `youtube-thumb-02.jpg` *任意* | 動画サムネ後半 | 670×378px |

> ロゴはCSSのみで再現（差し替え時は `.lp-logo__mark` 部を `<img>` に置換）

---

## Contact Form 7 連携メモ

`<form class="lp-form__inner">` 部分をCF7のショートコードに置換してください。
各 input の `name` 属性をCF7のタグ名と合わせると、後の集計が楽です。

### フィールドマッピング例

```text
[select* industry "" "項目を選択してください" "マンション管理組合" "管理会社" "その他"]
[text* company placeholder "例）株式会社〇〇〇〇〇〇"]
[text* your-name placeholder "例）山田　太郎"]
[email* your-email placeholder "例）info@example.com"]
[tel tel placeholder "例）000-0000-0000"]
[text address placeholder "例）神奈川県川崎市…"]
[select service "" "項目を選択してください" "玄関ドアリフォーム（カバー工法）" "無料診断・お見積り" "理事会向け資料のダウンロード"]
[textarea* your-message placeholder "例）築28年の…"]
[acceptance agree] プライバシーポリシーに同意する [/acceptance]
[submit "上記内容で送信する"]
```

> CF7のクラス名は CSS 側で `<form class="lp-form__inner">` を活かす想定です。
> CF7が生成する `<span class="wpcf7-form-control-wrap">` 等は補助CSSが必要になる場合があります（PC実装後に追記予定）。

---

## 実装進捗

- [x] HTML 骨組み（全セクション）
- [x] CSS モバイルファースト（〜414px）
- [ ] PC スタイル（@media min-width: 768px / 1024px）
- [ ] 画像差替え
- [ ] CF7 ショートコード差替え
- [ ] WP固定ページ用に `<style>` インライン化（最終納品形式）

---

## カラートークン

| Token | HEX | 用途 |
|---|---|---|
| `--lp-c-saxblue` | `#1AAEE5` | メイン青（見出し・アクセント） |
| `--lp-c-navy` | `#16458C` | 濃紺（強調） |
| `--lp-c-navy-deep` | `#0D2F5E` | フッター |
| `--lp-c-orange` | `#EE5A2E` | CTA・強調 |
| `--lp-c-accent` | `#FFC847` | リボン・装飾 |
| `--lp-c-bg-blue` | `#E6F4FC` | パネル背景 |
| `--lp-c-bg-sub` | `#F0F8FC` | セクション背景 |

## フォント

Google Fonts を `<link>` で読み込み:
- **Noto Sans JP**（日本語本文・見出し）400/500/700/900
- **Poppins**（英語Eyebrow / バッジ）600/700/900
- **Roboto**（数字 01〜05 / 価格 205,000） 900
