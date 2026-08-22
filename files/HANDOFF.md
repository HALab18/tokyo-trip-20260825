# 引き継ぎ指示書：東京観光ルートガイド → GitHub Pages公開

Claude.ai（チャット）でHALと作成した東京観光ルートガイドを、GitHub Pagesで
スマホから見られるWebアプリとして公開するための引き継ぎです。
tozan-plan スキル（登山計画のGitHub公開）と同じワークフローに揃えています。

## 前提
- GitHubアカウント: HALab18（登山計画リポジトリと同じアカウント）
- リポジトリ名: **tokyo-trip-20260825**
- 公開想定URL: `https://halab18.github.io/tokyo-trip-20260825/`
- 同梱ファイル: `tokyo-trip-20260825.html`（単一HTML完結、CSS/JS内包、スマホ対応、タブ4枚構成）

## ページの内容（タブ構成）
1. Day 1・火曜（8/25）: 東京ドーム→丸紅ギャラリー→横浜美術館
2. Day 2・水曜（8/26）: 新宿マルイ→六本木ヒルズ・森美術館（本命プラン）
3. Day2・代替案: 丸紅ギャラリーを朝一・10:00開館に合わせたプラン
4. Day2・代替案②: 丸紅ギャラリー80分＋新宿マルイ（ちいかわ）を最後に配置したプラン

いずれも実在確認済みの店舗・施設情報、地図直行ボタン（Googleマップ）、
公式サイトリンクを含む。デザインは再発明せず、このHTMLの構成・CSS・
クラス名をそのまま流用すること。

## 実行してほしいこと（tozan-planスキルのステップ4と同じ手順）

1. 作業ディレクトリに `tokyo-trip-20260825.html` として保存済み（本ファイル）
2. `index.html` にコピー
   ```bash
   cp tokyo-trip-20260825.html index.html
   ```
3. Git初期化・コミット
   ```bash
   git init
   git add index.html tokyo-trip-20260825.html
   git commit -m "東京観光ルートガイド 初版"
   ```
4. GitHubリポジトリ作成＆push
   ```bash
   gh repo create tokyo-trip-20260825 --public --source=. --remote=origin --push
   ```
5. GitHub Pages有効化
   ```bash
   gh api repos/HALab18/tokyo-trip-20260825/pages --method POST --field 'source[branch]=master' --field 'source[path]=/'
   ```
6. 公開URL `https://halab18.github.io/tokyo-trip-20260825/` をHALに伝える
   （反映まで数分かかる場合あり）

## 今後の修正時の注意
`tokyo-trip-20260825.html` を編集 → `index.html` へコピー → commit & push。
この2ファイル同期を忘れないこと（tozan-planスキルと同じ運用ルール）。

## 未確認・要確認のまま残っている点（本文中にも記載あり）
- タクシー運賃の具体的な改定内容（初乗り料金・加算距離）は未確認のため、
  ページ内では「目安、実際はメーターで確認」という表現に留めている
- 「サカモトデイズ展」（東京ドームシティ）自体の会期・会場詳細は未確認
  （ユーザーは予約済みとのことなので支障はないが、念のため触れておく）
