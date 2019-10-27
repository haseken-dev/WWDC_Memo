### Introducing Parameters for Shortcuts
[セッション動画](https://developer.apple.com/videos/play/wwdc2019/213/)

#### New in iOS 13
- SHortcuts app built-in to videos
- Parameters enable conversational shortcuts
- Users can customize the behavior of your shortcuts
- Update Add to Siri

#### 実装
- Shortcuts app
  - Shortcuts appはiOSに含まれるのでApp Storeからのインストールは必要ない
  - タップするか、Siriにいうだけで実行可能
  - "Appからのショートカット"という新しいセクションを設置。サードパーティappから関係のアクションをハイライト
  - 他のappのアクションと連携し、より便利にすることもできます。

- Add to Siri
  - フレーズの録音なしでショートカットを設定可能
    - ユーザーはフレーズを入力するか、提案を受け入れる形式
  - Add to Siriのシート上でショートカットの動作を調整可能

- 実装
  - Shortcut customization
    - Intentエディタから始める
    - Enumまたはカスタムタイプから選べる
    - User-facingにチェック
      - 追加した新しいパラメータにはdefaultで設定される
    - Display Nameを設定
      - ショートカットエディタ内にパラメータを表示するため
    - Siri、ショートかっとappから利用可能にするためには、Intent is user-configurableにチェックが必要
    - Summaryを設定する
  - Parameter resolution
    - Lifecycle of an Intent
      - Resolve(New)
        - Intentで定義済みの各パラメータを調べ、Intentハンドラにパラメータの解決を依頼。userに質問したりする
        - resolveMethodが自動生成されるので、IntentHandlingで呼び出す
        - IntentエディタでParameteの順序をドラッグ&ドロップで入れ替えることで、解決するparameterの順序を変更可能
        - Needs Valueを渡すと、Siriに質問するように促せる
        - ユーザーが回答した後、その回答を引数に再度Reslove Methodが実行される
      - confirm
      - Handle
        - Handling Voice Input参照
  - Related parameters
    -  Building Actions with Parameter Relationships参照
  - Dynamic options
    - Dynamic Optionにチェックを入れることで、質問する項目を自由に設定可能
    - チェックを入れるとMethodが自動生成される。
      - completionでは表示しうる値を返却する
        - needsValueを返却すると選択肢が表示される
      - defaultを設定できる
  - Outputs

#### Handling Voice Input
- Resolveフェーズでユーザーの入力に対して、コントロールを行う
- Resolve Valueは6つ
  - needsValue
    - ユーザーからの入力がない場合
    - IntentエディタでPromptを入力する必要がある
  - disambiguation
    - ユーザーに選択肢で入力させたい場合。(曖昧または選択肢が少ない など)
    - Intentエディタでカスタマイズできる
  - unsupported
    - ユーザ入力の値がサポート外の場合
    - Siriは再度ユーザーに問いかける
    - Intentエディタ->Validation Errorセクションで設定可能
  - confirmationRequired
    - ユーザーに入力した値が正しい値かどうかを聞くことができる
    - Intentエディタ -> Parameter Confirmationで設定可能
  - success
    - Siriが次のパラメータ処理に移行する
  - notRequired
    - パラメータ設定をスキップする

#### Building Actions with Parameter Relationships
  - Speakable Matchにユーザーに入力されても良いパターンを入れておく
    - 例えばpickup、ユーザーによってはtakeoutと呼ばれるため候補に入れておく
  - Parameter Relationships
    - Identified parent and child parameters
      - Intentエディタ -> Parametersで親typeも指定できる。
    - Established parameter Relationships
    - Updated summaries for each parameter combination

#### Building Actions with Outputs
- Intent Response
  - Intent実行の結果を論理的に表すもの
- 結果を定義できることで他のappとのshortcut連携をより強力にできる
