# ゆめいろべあーず ポータルサイト

## プロジェクト概要
「ゆめいろべあーず」ブランドのポータルサイト。くまのキャラクターを中心に、性格診断・マンガ・ショップなどのコンテンツへの導線を提供する。ターゲットは小学生の女の子～30代（子育て世代）。

## 関連サイト
- **せいかくしんだん**: https://shindan.yonde-web.com/（別リポジトリ `mbtidemo`）
- **ショップ**: https://suzuri.jp/YONDE

## 技術スタック
- 静的HTML/CSS/JS（サーバーサイド処理なし）
- GitHub Pages（カスタムドメイン: yonde-web.comのサブドメイン）
- フォント: Zen Maru Gothic

## ファイル構成
```
index.html              - トップページ（メインビジュアル + コンテンツカード一覧）
manga/index.html        - マンガページ（一覧 + 縦並びリーダー）
manga-image/            - マンガ画像
  YB_istj_infp/         - 第1話（ISTJ×INFP）
    YB_istj_infp-01.png - 表紙
    YB_istj_infp-02.png - 4コマ本編
    YB_istj_infp-03.png - キャラ解説
assets/                 - 共通アセット
  yumeiro_logo.png      - サイトロゴ
  yumeiro_bears.png     - くまたち集合画像
  yumeiro_back.png      - 背景画像
  yumeirobear_*.png     - 個別くまキャラ画像
robots.txt              - クロール指示
sitemap.xml             - サイトマップ
```

## デザイン方針
- 参考: ちいかわ公式サイト（グラフィック重視、親しみやすい）
- カラーパレット: mbtidemoのCSS変数を踏襲（ピンク・パープル・ミント系パステル）
- キャラクター重視 + カード型コンテンツ一覧
- ホバーアニメーション・スクロールフェードイン

## コンテンツ追加方法

### 新しいコンテンツカード（トップページ）
`index.html` の `.content-cards` 内に以下のHTMLを追加:
```html
<a href="リンク先" class="content-card">
  <div class="card-image-wrapper">
    <div class="card-image-bg bg-pink"><!-- bg-pink / bg-purple / bg-mint -->
      <img src="画像パス" alt="説明">
    </div>
  </div>
  <div class="card-body">
    <span class="card-label label-pink">ラベル</span><!-- label-pink / label-purple / label-mint -->
    <h3 class="card-title">タイトル</h3>
    <p class="card-desc">説明文</p>
    <div class="card-arrow">
      <span class="card-arrow-icon">▶</span>
      ボタンテキスト
    </div>
  </div>
</a>
```

### 新しいマンガエピソード
1. `manga-image/` に新フォルダを作成（例: `YB_entj_esfp/`）
2. 画像ファイルを配置（01=表紙, 02=本編, 03=解説）
3. `manga/index.html` の `mangaEpisodes` 配列に追加:
```js
{
  id: 'YB_entj_esfp',
  title: 'エピソードタイトル',
  characters: 'キャラA（ENTJ）× キャラB（ESFP）',
  folder: '../manga-image/YB_entj_esfp',
  pages: ['YB_entj_esfp-01.png', 'YB_entj_esfp-02.png', 'YB_entj_esfp-03.png']
}
```

## 注意事項
- ドメインは仮で `yumeiro.yonde-web.com` を設定。確定後に `canonical`, OGP, `sitemap.xml` のURLを一括変更すること
- 画像アセットは `mbtidemo` リポジトリから流用。元画像を変更した場合は手動同期が必要
