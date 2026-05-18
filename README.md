# 風のテラス行政書士事務所 サイト

名古屋市・愛知県の障害福祉サービス事業を専門サポートする行政書士事務所のホームページです。

## ディレクトリ構成

```
kazenoterrace/
├── index.html              # メインHTML（表示用）
├── CNAME                   # 独自ドメイン設定（kazenoterrace.com）
├── .nojekyll               # GitHub PagesでJekyllを無効化
├── README.md               # このファイル
├── assets/
│   ├── css/
│   │   └── style.css       # サイトのスタイルシート
│   ├── js/
│   │   └── main.js         # JavaScript（メニュー・スクロール演出など）
│   └── images/             # 画像格納用（ロゴ・プロフィール写真など）
└── content/                # 原稿管理（マークダウン形式）
    ├── 01-hero.md          # ヒーローセクション
    ├── 02-concerns.md      # お悩み訴求セクション
    ├── 03-strengths.md     # 当事務所の強み
    ├── 04-services.md      # サービス内容
    ├── 05-pricing.md       # 料金プラン
    ├── 06-flow.md          # ご依頼の流れ
    ├── 07-profile.md       # 行政書士紹介
    ├── 08-office.md        # 事務所概要
    └── 09-contact.md       # お問い合わせ
```

## 原稿の更新方法

原稿は `content/` 配下の各マークダウンファイルで管理しています。<br>
原稿を修正する場合は、まず該当する `.md` ファイルを編集し、その内容を `index.html` の対応セクションに反映してください。

「原稿のたたき台はマークダウンで管理 → 確定したら index.html に反映」というワークフローです。

## ダミーから本番情報への置き換え

現状、以下の項目はダミー値（`××`）となっています。本番公開前に一括置換してください。

| 項目 | 検索文字列の例 |
| :--- | :--- |
| 代表氏名 | `×××× ××××` |
| 郵便番号 | `〒×××-××××` |
| 住所 | `愛知県名古屋市×××区××××` |
| 電話番号 | `×××-××××-××××` |
| 行政書士会の登録番号 | `第××××××××号` |
| 経歴の年・組織名 | `20××年` `××法人` |
| 経験年数 | `××年` |

`index.html` 内のダミー値を、確定情報に一括置換してください。<br>
（VSCode等のエディタの「全体検索・置換」機能で簡単に対応できます。）

## GitHub Pages 公開手順

### 1. GitHubリポジトリの作成
1. GitHubで `kazenoterrace.github.io` という名前のリポジトリを作成（**Public**）
2. このディレクトリの内容をリポジトリにpush

```bash
cd kazenoterrace
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/kazenoterrace.github.io.git
git push -u origin main
```

### 2. GitHub Pagesの有効化
1. リポジトリの **Settings** → **Pages** に移動
2. **Source**: Deploy from a branch
3. **Branch**: `main` / `(root)` を選択して **Save**

これで `https://<your-username>.github.io/` または `https://kazenoterrace.github.io/` でアクセス可能になります。

### 3. 独自ドメイン（kazenoterrace.com）の設定
独自ドメインを使用するには、以下の2点を行います。

#### ① DNS設定（ドメイン管理サービス側）
お使いのDNS管理サービス（お名前.com、Cloudflare、ムームードメイン等）で以下のレコードを追加します。

**Aレコード（apex domain用）**
```
タイプ: A
ホスト: @  (または kazenoterrace.com)
値: 185.199.108.153
値: 185.199.109.153
値: 185.199.110.153
値: 185.199.111.153
```

**CNAMEレコード（www用）**
```
タイプ: CNAME
ホスト: www
値: <your-username>.github.io
```

#### ② GitHub Pages 側の設定
1. リポジトリの **Settings** → **Pages**
2. **Custom domain** に `kazenoterrace.com` を入力して **Save**
3. DNS伝播後（数分〜数時間）、**Enforce HTTPS** にチェックを入れる

なお、リポジトリ直下に既に `CNAME` ファイルを配置済みのため、上記②はpush時に自動反映される場合もあります。

### 4. デプロイ完了
DNS反映後、`https://kazenoterrace.com` にアクセスするとサイトが表示されます。

## カスタマイズの注意点

### カラー変更
カラーは `assets/css/style.css` の冒頭にある CSS変数（`:root` 内）で一元管理しています。<br>
緑系のトーンを変更したい場合は、以下の変数を調整してください。

```css
--color-primary: #2d5a3d;        /* 深緑（信頼） */
--color-primary-light: #4a8061;
--color-accent: #c8a55b;         /* 落ち着いた金色（上質感） */
```

### ロゴ画像への差し替え
現在、ロゴは「風」の文字を丸い円で囲んだプレースホルダーです。<br>
本番のロゴ画像を入手後、以下の手順で差し替えてください。

1. ロゴ画像を `assets/images/logo.png` （または `.svg`）として保存
2. `index.html` の `<span class="logo-mark">風</span>` を `<img src="assets/images/logo.png" alt="風のテラス行政書士事務所">` に置き換え
3. `.logo-mark` のCSS（円形、緑背景、`::after`のラベル）も合わせて削除またはコメントアウト

### プロフィール写真の差し替え
1. 写真を `assets/images/profile.jpg` として保存
2. `index.html` 内の `.profile-photo-placeholder` 部分を `<img src="assets/images/profile.jpg" alt="代表行政書士">` に置き換え

## サイト構成（9セクション）

1. ヒーロー（トップビジュアル）
2. こんなお悩みありませんか？
3. 当事務所の強み（行政書士活用の3つのメリット）
4. サービス内容（新規申請メイン／変更・運営サポートサブ）
5. 料金プラン
6. ご依頼の流れ
7. 行政書士紹介
8. 事務所概要
9. お問い合わせ

## 技術スタック
- HTML5 / CSS3 / Vanilla JavaScript
- Webフォント：Noto Serif JP / Noto Sans JP / Shippori Mincho（Google Fonts）
- 外部ライブラリ：なし（軽量・高速）

## ライセンス
本サイトのコンテンツの著作権は、風のテラス行政書士事務所に帰属します。
