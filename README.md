# retrosurvivor-legal

スマホゲーム RetroSurvivor（iOS / Android）のプライバシーポリシー、利用規約、サポートのページ。
GitHub Pages（リポジトリ `hiro0211/retrosurvivor-legal`、`main` ブランチの `/`）で配信する。
構成と書き方は `hiro0211/minicalc-legal` に合わせた。施行日は 2026-10-19。

この `legal/` フォルダは RetroSurvivor 本体とは別の git リポジトリとして扱う。

## 公開 URL

2026-10-19 に下の 7 ページが HTTP 200 を返すことを curl で確認した（Pages: `main` の `/`、HTTPS 強制あり）。

- トップ: https://hiro0211.github.io/retrosurvivor-legal/
- プライバシーポリシー（日本語）: https://hiro0211.github.io/retrosurvivor-legal/privacy/
- プライバシーポリシー（英語）: https://hiro0211.github.io/retrosurvivor-legal/privacy/en/
- 利用規約（日本語）: https://hiro0211.github.io/retrosurvivor-legal/terms/
- 利用規約（英語）: https://hiro0211.github.io/retrosurvivor-legal/terms/en/
- サポート（日本語）: https://hiro0211.github.io/retrosurvivor-legal/support/
- サポート（英語）: https://hiro0211.github.io/retrosurvivor-legal/support/en/

## 管理画面に入力する URL

| 入力先 | 入力する URL |
|---|---|
| AdMob の「プライバシーとメッセージ」（GDPR メッセージなど）のプライバシーポリシー URL | https://hiro0211.github.io/retrosurvivor-legal/privacy/en/ |
| App Store Connect の「プライバシーポリシー URL」 | 日本語ストア: https://hiro0211.github.io/retrosurvivor-legal/privacy/ ／ 英語ストア: https://hiro0211.github.io/retrosurvivor-legal/privacy/en/ |
| App Store Connect の「サポート URL」 | https://hiro0211.github.io/retrosurvivor-legal/support/ （英語は `/support/en/`） |
| Google Play Console の「プライバシー ポリシー」 | https://hiro0211.github.io/retrosurvivor-legal/privacy/ |

AdMob の同意メッセージは EEA・英国・米国の利用者に表示されるため、英語版の URL を推す。
日本語版を入れても条件は満たす（どちらのページにも相手の言語への切替がある）。

## ファイル構成

```
.
├── index.html            # トップ（日本語と英語の入口）
├── 404.html
├── privacy/index.html    # プライバシーポリシー（日本語）
├── privacy/en/index.html # Privacy Policy（英語）
├── terms/index.html      # 利用規約（日本語）
├── terms/en/index.html   # Terms of Use（英語）
├── support/index.html    # サポート（日本語）
├── support/en/index.html # Support（英語）
├── assets/css/style.css
├── assets/icons/favicon.svg
├── .nojekyll
└── README.md
```

## ページに書いた前提（アプリの実装と食い違ったら、ページを直す）

- アカウントなし、サーバーなし。ゲームの記録と設定は端末内だけに保存する。
- 広告は Google AdMob（バナー、インタースティシャル、リワード）。同意は UMP SDK（GDPR、iOS の IDFA 説明と ATT、米国の州の規制）。
- 分析 SDK とクラッシュ報告 SDK は使わない。入れるときはプライバシーポリシーの 2 章、4 章、12 章を直す。
- 広告削除の課金は「今後導入する場合」として書いた。入れるときは両ページの該当章を直す。
- 対象年齢は「13歳未満を対象にしない」（minicalc-legal と同じ書き方）。AdMob の子ども向け設定とストアの年齢区分をこれに合わせる。
- 連絡先は appsupport0326@gmail.com。minicalc-legal は連絡先が `[SUPPORT_EMAIL]` のまま公開されていたため、同じアカウントの walkcraft-legal と rewire-support で公開済みのアドレスを使った。住所・電話番号・氏名は載せていない。

## アプリ側でやること（ページの記載どおりにするため）

- 設定画面に「プライバシー設定」ボタンを置く。`privacyOptionsRequirementStatus` が REQUIRED のときだけ表示し、押したら `AdMob.showPrivacyOptionsForm()` を呼ぶ（サポートページの 2-1 の手順と一致させる）。
- 設定画面にプライバシーポリシー、利用規約、サポートへのリンクを置く（Apple 5.1.1(i) と Google Play のユーザーデータポリシーがアプリ内のリンクを求める）。
- iOS の Info.plist に `NSUserTrackingUsageDescription` を書く。

## 根拠にした公式ページ（2026-10-19 に確認）

Google AdMob と Google の同意ポリシー
- Google Publisher Policies（プライバシーの開示。パートナーサイトのページへのリンクで開示を満たせる）: https://support.google.com/publisherpolicies/answer/10502938
- AdMob のポリシーの入口: https://support.google.com/admob/answer/6128543
- Google のパートナーのサイトやアプリでの情報の使用: https://policies.google.com/technologies/partner-sites
- EU ユーザーの同意ポリシー: https://www.google.com/about/company/user-consent-policy/
- UMP SDK（プライバシー設定の入口を置く要件）: https://developers.google.com/admob/ump/android/quick-start ／ https://developers.google.com/admob/ump/ios/quick-start
- 米国の州の規制メッセージ: https://support.google.com/admob/answer/10862202
- 米国の州のプライバシー（SDK 側の扱い）: https://developers.google.com/admob/android/privacy/us-states
- 子ども向けの設定（tagForChildDirectedTreatment など）: https://developers.google.com/admob/android/targeting

Apple
- App Store Review Guidelines 5.1.1 / 5.1.2: https://developer.apple.com/app-store/review/guidelines/
- App のプライバシーに関する詳細（プライバシー表示）: https://developer.apple.com/app-store/app-privacy-details/
- ユーザーのプライバシーとデータの使用（ATT）: https://developer.apple.com/app-store/user-privacy-and-data-use/
- Google Mobile Ads SDK の iOS 向けデータ開示: https://developers.google.com/admob/ios/privacy/data-disclosure

Google Play
- ユーザーデータポリシー（プライバシーポリシーの記載事項とページの条件）: https://support.google.com/googleplay/android-developer/answer/10144311
- データセーフティ: https://support.google.com/googleplay/android-developer/answer/10787469
- Google Mobile Ads SDK の Play 向けデータ開示: https://developers.google.com/admob/android/privacy/play-data-disclosure
- ファミリー ポリシー（対象年齢）: https://support.google.com/googleplay/android-developer/answer/9893335

## 確認できなかったこと

- 米国の州の規制メッセージで、アプリ側にプライバシーポリシーへのリンクが必須かどうか（公式ページに明記がなかった）。
- App Store Review Guidelines の 5.1 より後ろの全文。
- 弁護士などの専門家による確認はしていない。

## ローカルで見る

```bash
cd /Users/arimurahiroaki/RetroSurvivor/legal
python3 -m http.server 8000
# http://localhost:8000/ を開く（404.html のリンクは公開 URL 前提）
```

## 更新するとき

- 内容を変えたら、各ページの「最終更新日 / Last updated」を直す。
- 大きな変更はアプリ内でも知らせる。
- 履歴は git log で追う。
