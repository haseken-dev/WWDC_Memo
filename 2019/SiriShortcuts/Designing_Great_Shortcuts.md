### Designing Great Shortcuts
[セッション動画](https://developer.apple.com/videos/play/wwdc2019/806/)
#### Choosing features
- Use Cases
  - Accelerate an action
  - Present concise information
  - Useful in multi-step shortcuts
- Siri SuggestionはiOS 12から導入済
- appの機能を列挙し、声で操作することを考えてみるのが良い
  - Soup Chefのメニュー閲覧
    - スクロールもある、メニューも変わる、難しいと思われる
  - スープの注文状況
    - 配達までに数日かかるような場合。スープの場合はすぐに届くので、あまり利用シーンはない
  - スープの注文
- Good Siri Voice Shortcuts
  - 重要な機能であること
  - 繰り返し使うこと
  - 視覚やタップに頼らず声が使えること
  - 起動の機会が多いこと

#### Discoverability
- 「Add to Siri」ボタンは設置しすぎないこと
  - デザインが良くても見辛い、使いにくくなる
- 「Add to Siri」ボタン
  - 角の丸みが調整可能
  - ユーザーのDark,Lightモードに合わせて色が変わる
- 独自にボタンをデザインし、作成することもできるが、機能を再現することが重要
- 起動文言
  - 3語以内にする
  - 固有名詞 or 動詞 と 目的語に限定
  - 利用シーンで起動したいパラメータが変わる場合は、Conversationalに尋ねるようにする

#### Siri interactions
- Siriとの会話を想定してパラメータの質問を考えるのが良い
- 想定される会話を全てメモしてみる
  - ユーザーが想定外のことを行った場合も想定
  - 最終的にはフローチャートのようになるはず
- prompt
  - 基本
    - 質問として書き、的確な答えを導くいい周りにするべき
    - 選択肢を表示することで曖昧性を消すことも必要
    - HomePodなどでは音声のみの案内になるので、選択肢を読み上げるようにすると良い
      - 読み上げるのは違いを表すなど短くするのも良い
    - 選択肢に同義語を与えるのが良い
  - Parameter Confirmation
    - 重要な確認が必要な場合、利用できる
    - 例外的な利用
  - Action Confirmation
    - カスタマイズ可能なビジュアルUIで表示
    - HomePodなどディスプレイがない場合は音声用のダイアログも用意
  - Response
    - 追加の詳細情報はカスタムUIで提示
    - 音声の場合は詳細が必要
  - Categories
    - actionに最も近いものを設定
    - 設定したcategoryに近い内容でdefault質問するので、確認ダイアログに質問を含めないこと
    - 応答も同様。
  - Errors
    - 無効とわかっている選択肢は表示しないこと
  - Continuing in App
    - appで操作が必要な場合、SiriのビジュアルUI全体を起動ボタンと考えて起動させる
    - タップしたら適切な画面が表示されるようにする
  - Language is UI
- ガイドライン
  - Siri発話内容にappは含めないこと。
  - ユーザー名も含めないこと
  - 一人称代名詞は避ける
