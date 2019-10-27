### Bulding Great Shortcuts
[セッション動画](https://developer.apple.com/videos/play/wwdc2019/805/)

#### Configuration
- パラメータ
  - Intent Definition Fileで定義
  - shortcut appでユーザー入力がなければ、Display Nameを表示
  - 表示名は常に大文字に(英語のみ？)
- Parameter summary
  - 動詞で始まるようにするべき
  - App名は不要
  - 短くし、必要最小限のパラメータのみ記述
    - 他のパラメータは「もっと見る」から編集可能

#### Discoverability
- Appないでshortcutは設定させるのが良い
- When I Sayの値はIntents->suggestedInvocationPhraseで設定可能
  - アクションをわかりやすい短い文章で
- appで設定させる場合、わかっている範囲でたくさんの情報をIntentsに設定すること
  - すぐに設定ができ、また呼び出し易くなる
- 初めてのユーザはshortcut appのギャラリーを見る
  - よく使うappが出てきやすい
- Donatationが有効
  - Key Parameterを設定する
    - Suggestionsで表示される
  - Imageをセットすることで、画像も表示可能。設定されてない場合はapp icon

#### Input and output
- iOS 13ではactionの出力を制御でき、他のshortcutが利用できる
- 制御することで、同一appでもアクション連携ができる
- ただし、shortcut appからしか作れない
