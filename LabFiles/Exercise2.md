# 演習 2: エージェント フローとマルチエージェント オーケストレーション

### 推定所要時間: 30 分

## 概要

この演習では、Safe Travels エージェントをビジネス プロセス自動化で強化し、マルチエージェント オーケストレーション機能を体験します。Microsoft Teams と統合する包括的な旅行承認ワークフローを作成し、既存の旅行アシスタントとシームレスに連携する専門的な Leave Manager エージェントを構築します。

この演習は、実ビジネス シナリオでの会話型 AI の力を示します。エージェントが実際のビジネス プロセスをトリガーし、相互にコラボレーションし、エンドツーエンドの自動化ソリューションを提供する方法を確認できます。最後に、Safe Travels エージェントが休暇関連のクエリを専門的な Leave Manager エージェントに自動的にルーティングし、自動化された Teams 通知を通じて旅行承認を処理する洗練されたマルチエージェント システムが完成します。

## 目的

次のタスクを完了します:

- タスク 1: Teams ワークスペースを設定し、エージェント フロー トリガーを初期化する
- タスク 2: フロー アクションと Teams メッセージ投稿を設定する
- タスク 3: Travel Approval フローをエージェントに統合し、エンドツーエンドでテストする
- タスク 4: Leave Manager エージェントを構築し、マルチエージェント オーケストレーションを確立する

## タスク 1: Teams ワークスペースを設定し、エージェント フロー トリガーを初期化する

このタスクでは、旅行承認ワークフローの基盤を構築します: Teams ワークスペースを作成し、必要な入力でエージェント フロー トリガーを初期化します。これにより、後続の自動化と統合の準備が整います。

1. **Microsoft Teams** に移動し、**Chat (1)** セクションに移動し、**New (2)** ドロップダウンをクリックして **New team (3)** を選択し、旅行承認専用のワークスペースを作成します。

   ![Open Teams](../media/ex2-travel-g1.png)

   >**Teams Integration Foundation:** 専用チームとチャネル構造を作成することで、旅行承認リクエストが整理され、適切なステークホルダーにレビューと処理のためにルーティングされます。

1. 新しいチームを次の詳細で構成し、**Create (3)** をクリックします。

   | Key | Value |
   |-----|-------|
   | Team name **(1)** | `HR Team` |
   | First channel **(2)** | `Travel Approvals` |

   ![Create Team](../media/ex2-travel-g2.png)

1. **Add members to HR Team** ウィンドウで、このデモンストレーションではメンバーを追加せずに続行するために **Skip** を選択します。

   ![Team Details](../media/ex2-travel-g3.png)

1. **Copilot Studio** に戻り、左メニューから **Flows (1)** を選択します。**New agent flow (2)** をクリックして新しい自動化ワークフローを作成します。

   ![Skip Members](../media/saf-tra-cor-v2-g16.png)

1. **Add a trigger** ペインで **Skills (1)** を検索し、**When an agent calls the flow (2)** を選択します。

   ![](../media/saf-tra-cor-v2-g17.png)

   > **Workflow Foundation:** このトリガーは、エージェントがユーザー会話に基づいてビジネス プロセスを自動的に開始できるようにし、会話型 AI とビジネス運用間のシームレスな統合を作成します。

1. トリガー ノードの下にある **Add an input** をクリックして、エージェントがワークフローに渡すデータ パラメータを定義します。

   ![](../media/saf-tra-cor-v2-g18.png)

1. 最初の入力パラメータのデータ型として **Number** を選択して、従業員識別をキャプチャします。

   ![New Agent Flow](../media/saf-tra-cor-v2-g19.png)

1. 最初の入力パラメータを設定します:
   - **Name:** **Employee ID (1)** を入力します
   - **Add an input (2)** をクリックして 2 番目のパラメータを作成します。

      ![Add Trigger](../media/ex2-travel-g8.png)

1. 2 番目の入力パラメータのデータ型として **Text** を選択して、旅行詳細をキャプチャします。

   ![Select Trigger](../media/ex2-travel-g9.png)

1. 2 番目の入力パラメータに **Purpose** という名前を付けて、旅行リクエストのビジネス理由をキャプチャします。

   ![Add Input](../media/ex2-travel-g10.png)

## タスク 2: フロー アクションと Teams メッセージ投稿を設定する

このタスクでは、Microsoft Teams アクション、動的コンテンツ、応答処理を追加し、Travel Approval フローを公開して名前を付けます。

1. トリガー ノードの下にある **Add (1)** アイコンをクリックして、ワークフロー自動化に新しいアクション ステップを挿入します。

   ![Employee ID Input](../media/saf-tra-cor-v2-g20.png)

1. Microsoft Teams 統合を検索するために **Post message in a chat or channel (1)** と入力し、利用可能な Microsoft Teams アクションから **select (2)** を選択します。

   ![Add Second Input](../media/ex2-travel-g12.png)

1. **Sign in** を選択してワークフロー統合を認証および承認し、Microsoft Teams 接続を確立します。

   ![Purpose Input](../media/ex2-travel-g13.png)

1. **ODL_User (1)** アカウント資格情報を選択して、Microsoft Teams 接続を認証および確立します。

   ![Add Action](../media/ex2-travel-g14.png)

1. 次のペインで **Allow Access** をクリックして、エージェントへの接続アクセスを許可します。

   ![](../media/sfimg10.png)

1. Teams メッセージ投稿アクションを次のパラメータで構成します。

   | Key | Value |
   |-----|-------|
   | Post as **(1)** | Flow bot |
   | Post in **(2)** | Channel |
   | Team **(3)** | HR Team |
   | Channel **(4)** | Travel Approvals |
   | Message **(5)** | `Travel request from Employee ID: [Employee ID], Purpose: [Purpose]` |

   ![Search Teams](../media/ex2-travel-g15.png)

   > **Teams Integration Benefits:** この構成により、旅行承認リクエストが指定された HR チーム チャネルに自動的に投稿され、適切な監査証跡を持つ集中化された承認ワークフローが作成されます。

1. メッセージ ボックスで **[Employee ID] (1)** を強調表示し、**Dynamic content (2)** アイコンをクリックして Employee ID 変数を挿入します。

   ![Post Message Action](../media/ex2-travel-g16.png)

1. **Dynamic content** パネルから、"When an agent calls the flow" セクションの下にある **Employee ID** を選択します。

   ![Sign In](../media/ex2-travel-g17.png)

1. メッセージで **[Purpose] (1)** を強調表示し、**Dynamic content (2)** アイコンをクリックして Purpose 変数を挿入します。

   ![Login Credentials](../media/ex2-travel-g18.png)

1. 両方の動的値 **Employee ID** と **Purpose (1)** が正しく追加されていることを確認し、**Add (2)** アイコンをクリックして次のアクションを挿入します。

   ![Configure Teams](../media/ex2-travel-g19.png)

1. **Add an action** ペインで **Skills (1)** を検索し、**Respond to the agent (2)** を選択します。

   ![Message Configuration](../media/saf-tra-cor-v2-g21.png)

1. **Respond to the agent** アクションの下にある **Add an output (1)** をクリックして、戻りメッセージを定義します。

   ![Dynamic Content](../media/ex2-travel-g21.png)

1. エージェント応答の出力タイプとして **Text (1)** を選択します。

   ![Parameters Complete](../media/ex2-travel-g22.png)

1. 出力構成の次の詳細を入力します。

   | Key | Value |
   |-----|-------|
   | Name **(1)** | `Output` |
   | Value **(2)** | `Request submitted` |
   | Description **(3)** | `Confirmation message for travel request` |

   ![Close Parameters](../media/ex2-travel-g23.png)

1. 公開する前に、現在のフロー構成を保存するために **Save draft (1)** をクリックします。

   ![Add Second Action](../media/ex2-travel-g24.png)

1. ページ上部に **“We saved your draft flow. You can test and run it after you publish.”** という確認メッセージが表示されることを確認します。

   ![Respond to Agent](../media/ex2-travel-g25.png)

1. エージェント フローを利用可能にするために **Publish** をクリックします。

   ![Configure Output](../media/ex2-travel-g26.png)

1. **Overview (1)** タブに移動し、**Edit (2)** をクリックしてエージェント フローの詳細を変更します。

   ![Publish Flow](../media/ex2-travel-g28.png)

1. フロー名として **Travel Approval Flow (1)** を入力し、**Save (2)** をクリックして変更を適用します。

   ![Flow Published](../media/ex2-travel-g29.png)

<validation step="79aacbd4-3125-426d-8b4f-fc9a29efaa87" />
 
> **おめでとうございます**。タスクが完了しました。次は検証です。手順は次のとおりです:
> - 該当するタスクの Validate ボタンをクリックします。成功メッセージが表示されたら、次のタスクに進んでください。
> - 表示されない場合は、エラーメッセージを注意深く読み、ラボ ガイドの手順に従ってステップを再試行してください。
> - サポートが必要な場合は、cloudlabs-support@spektrasystems.com までお問い合わせください。24 時間 365 日対応しています。

## タスク 3: Travel Approval フローをエージェントに統合してテストする

このタスクでは、公開されたフローを Safe Travels エージェントの新しいトピックに接続し、変数をマッピングし、更新を公開し、Teams 検証を含むエンドツーエンド実行をテストします。

1. **Copilot Studio** で **Safe Travels Agent** を開き、ドロップダウン メニューから **Topics (1)** を選択します。

   ![Overview Tab](../media/ex2-travel-g30.png)

1. **Topics** タブで **Add a topic (1)** をクリックし、ドロップダウン メニューから **Add from description with Copilot (2)** を選択します。

   ![Add to Agent](../media/ex2-travel-g31.png)

1. 次の詳細で Travel Approval トピックを作成し、**Create (3)** をクリックします。

   | Key | Value |
   |-----|-------|
   | Name your topic **(1)** | `Travel Approval` |
   | Create a topic to... **(2)** | `This topic should get the Employee ID (Number) and Purpose of travel (Text) details from the user and invoke the Tool "Request Travel Approval Flow"` |

   ![](../media/cor-g-g12.png)

1. 既存のメッセージ ノードを次のように削除します:  
   - **More options (1):** メッセージ ノードの **ellipsis (…)** アイコンをクリックします。  
   - **Delete (2):** **Delete** を選択してトピック フローからメッセージを削除します。  

      ![](../media/cor-g-g16.png)

1. トピック編集キャンバスで、**Question** ノードの下にある **plus (+)** アイコンをクリックして新しいアクションを追加します。

   ![Confirm Publish](../media/cor-g-g17.png)

1. Travel Approval Flow ツールを次のように追加します:  
   - **Add a tool (1):** オプション メニューから **Add a tool** を選択します。  
   - **Travel Approval Flow (2):** ツールの一覧から **Travel Approval Flow** を選択し、トピックにリンクします。  

      ![](../media/cor-g-g18.png)

1. **Power Automate inputs (2)** セクションで、**Employee ID (Number)** の横にある変数ピッカー **(1)** をクリックし、**Select a variable** パネルから **EmployeeID (2)** を選択します。

      ![](../media/cor2-gs-g8.png)

1. 同じ手順を実行し、**Purpose (String)** フィールドに **PurposeOfTravel** を選択します。

1. 両方の変数が正しくマッピングされると、画像に示されているように **Employee ID (Number)** が **EmployeeID** に、**Purpose (String)** が **PurposeOfTravel** にマッピングされます。

   ![](../media/cor-g-g19.png)

1. 出力をマッピングした後、**Action** ノードの下にある **plus (+)** アイコンをクリックして次のステップを追加します。
 
   ![](../media/cor-g-g20.png)

1. アクション メニューから **Send a message** を選択し、ユーザーに確認メッセージを表示します。
 
   ![](../media/cor-g-g21.png)

1. **Message** ボックスで **variable picker (1)** をクリックし、リストから **Output (2)** を選択してメッセージに挿入します。  

   ![Request Submitted](../media/ex2-travel-g55.png)

1. **Save** ボタンをクリックしてトピック構成を保存します。  

   ![Teams Notification](../media/ex2-travel-g56.png)

1. **Overview (1)** タブに移動し、**Publish (2)** をクリックしてエージェントの更新をライブにします。  

1. **Publish this agent** ダイアログ ボックスで **Publish** をクリックして、エージェントを確定してデプロイします。  

   ![Teams Notification](../media/saf-tra-cor-v2-g22.png)

1. エージェントが正常に公開されたら、**Test** をクリックして Copilot エージェントを検証および操作します。  

   ![Teams Notification](../media/ex2-travel-g59.png)

1. テスト チャットで次の **prompt (1)** を入力し、**Send (2)** を選択します。

   ```
   I need travel approval
   ```

   ![](../media/cor-g-g23.png)

1. **What is your Employee ID?** と表示されたら、次の **response (1)** を入力し、**Send (2)** を選択します。

   ```
   117
   ```

   ![](../media/ex2-travel-g61.png)

1. **What is the purpose of your travel?** と尋ねられたら、次の **response (1)** を入力し、**Send (2)** を選択します。

   ```
   Client meeting
   ```

   ![](../media/ex2-travel-g62.png)

1. Microsoft Teams 接続アクセスを求められたら、**Allow** をクリックして統合を承認し、フローが Teams に旅行リクエストを投稿できるようにします。

   ![](../media/ex2-travel-g63.png)

1. Microsoft Teams 接続が承認されたら、確認メッセージ **Request submitted** が表示されることを確認します。これは旅行承認リクエストが正常に処理されたことを示します。

   ![](../media/ex2-travel-g64.png)

1. Microsoft Teams にメッセージが投稿されていることを次の手順で確認します:  
   - **Chat (1):** **Chat** タブを開きます。  
   - **Team (2):** **HR Team** を選択します。  
   - **Channel (3):** **Travel Approvals** を開きます。  
   - **Message (4):** 投稿が次のように表示されていることを確認します:  
     `Travel request from Employee ID: 117, Purpose: Client meeting`.  

      ![](../media/ex2-travel-g65.png)

      > **Flow Validation:** 旅行承認フローを正常にテストすると、エージェントが実際のビジネス プロセスをトリガーし、エンタープライズ コラボレーション ツールと統合できることが確認されます。

## タスク 4: マルチエージェント オーケストレーションを確立する

このタスクでは、分散型 AI システムの力を学びます。専門エージェントが特定のビジネス ドメインを担当しながら、インテリジェントなルーティングとコラボレーションを通じて統一されたユーザー エクスペリエンスを維持します。

1. 左メニューから **Agents** を選択し、**Leave manager agent** に移動します。

   ![](../media/sfimg11.png)

1. 上部の **menu** から **Topics** を選択し、エージェントの会話トピックを作成または管理します。  

   ![](../media/ex2-travel-g75.png)

1. **Add a topic (1)** をクリックし、**Add from description with Copilot (2)** を選択して、自然言語の説明からトピックを自動生成します。  

   ![](../media/ex2-travel-g76.png)

1. 次の詳細で **Leave Balance Checker** トピックを作成し、**Create (3)** をクリックします。

   | Key | Value |
   |-----|-------|
   | Name your topic **(1)** | `Leave Balance Checker` |
   | Create a topic to... **(2)** | `Get the Employee ID from the user and check and reply with the leave balance based on the tracker added as knowledge source.` |

   ![](../media/ex2-travel-g80.png)

1. トピック フローを確認し、**message** ノードのメニューをクリックして **...** を選択し、**Delete** を選択します。

   ![](../media/sfimg17.png)

1. 完了したら、**+** をクリックして新しいノードを追加します。

   ![](../media/sfimg18.png)

1. リストから **Advanced** を選択し、**Generative answers** をクリックします。

   ![](../media/sfimg19.png)

1. Generative answers ノードで **...** オプションを選択します。

   ![](../media/sfimg21.png)

1. 変数リストから **EmployeeID** を選択します。

   ![](../media/sfimg20.png)

1. 完了したら、**edit** をクリックしてナレッジ ソースを構成します。

   ![](../media/sfimg22.png)

1. サイド パネルで **Search only selected sources** オプションを切り替え、リストから **Leave balance Tracker.xlsx** を選択します。

   ![](../media/sfimg23.png)

1. 構成が完了したら、上部メニューの **Save** をクリックしてトピックを保存します。

   ![](../media/sfimg24.png)

1. トピックの保存に成功したら、**Test** をクリックしてテスト ペインを開き、Leave Manager Agent の応答フローを確認します。  

   ![](../media/ex2-travel-g90.png)

1. テスト チャットで次の **prompt (1)** を入力し、**Send (2)** を選択します。

   ```
   Check Leave balance
   ```

   ![](../media/ex2-travel-g84.png)

1. プロンプトが表示されたら、次の **Employee ID (1)** を入力し、**Send (2)** を選択します。

   ```
   1234
   ```

   ![](../media/ex2-travel-g85.png)

1. Leave Manager agent が Employee ID 1234 (John Doe) の残りの休暇残高を **2 days** と表示する様子を確認します。これは、専門エージェントがシームレスに連携するマルチエージェント オーケストレーションの実例です **(1)**。

   ![](../media/sfimg13.png)

1. **Publish (1)** をクリックしてエージェントを公開します。

1. ダイアログ ボックスで再度 **Publish** をクリックします。

   ![](../media/sfimg8.png)

1. 公開が完了したら、**Safe Travels Agent** に戻ります。

   ![](../media/saf-tra-cor-v2-g14.png)

1. **+5 (1)** メニューをクリックして追加オプションにアクセスします。**Agents (2)** を選択して、トピック、アクティビティ、分析、チャネルなどの他の機能にアクセスします。

   ![](../media/ex2-travel-g95.png)

1. **Add** をクリックして、既存の Safe Travels Agent と連携する新しいエージェントを作成します。

   ![](../media/ex2-travel-g96.png)

1. 使用可能なエージェントの一覧から **Leave Manager Agent** を選択して接続します。

   ![](../media/ex2-travel-g98.png)

1. エージェント構成を確認し、**Add and configure** をクリックして接続を完了します。

   ![](../media/sfimg14.png)

1. **Safe Travels Agent** インターフェイスで **Agents** タブに移動し、**Settings** をクリックしてエージェント設定を構成します。

   ![](../media/sfimg15.png)

1. **Generative AI (1)** 設定に移動し、オーケストレーションに **Yes (2)** が選択されていることを確認し、**Save (3)** をクリックします。

   ![](../media/ex2-travel-g104.png)

1. さらに **Agent (1)** タブで **Leave Manager Agent (2)** を選択します。

   ![](../media/ex2-travel-g108.png)

1. **Publish** をクリックして Leave Manager Agent を公開します。

   ![](../media/ex2-travel-g109.png)

1. 公開ダイアログで **Publish** をクリックして確認します。

   ![](../media/ex2-travel-g110.png)

1. エージェント一覧から **Safe Travels Agent (2)** に戻ります。

   ![](../media/ex2-travel-g111.png)

1. 連携された Leave Manager Agent を含むように Safe Travels Agent を公開するために **Publish** をクリックします。

   ![](../media/ex2-travel-g112.png)

1. 公開ダイアログで **Publish** をクリックして確認します。

   ![](../media/ex2-travel-g113.png)

1. **Safe Travels Agent** のエージェント機能をテストするために **Test** をクリックします。

1. テスト チャットで次の **prompt (1)** を入力し、**Send (2)** を選択します。

   ```
   Check Leave balance
   ```

   ![](../media/sfimg16.png)

1. プロンプトが表示されたら、次の **Employee ID (1)** を入力し、**Send (2)** を選択します。

   ```
   1234
   ```

   ![](../media/ex2-travel-g85.png)

   > **Multi-Agent Success:** Safe Travels エージェントと Leave Manager エージェント間のシームレスな引き継ぎは、専門エージェントが協力して包括的なビジネス ソリューションを提供する正常なオーケストレーションを示します。

<validation step="e50761be-041a-4631-8e82-ca3952b8aa3a" />
 
> **おめでとうございます**。タスクが完了しました。次は検証です。手順は次のとおりです:
> - 該当タスクの Validate ボタンをクリックします。成功メッセージが表示されたら、次のタスクに進んでください。
> - 表示されない場合は、エラーメッセージを注意深く読み、ラボ ガイドの手順に従ってステップを再試行してください。
> - サポートが必要な場合は、cloudlabs-support@spektrasystems.com までお問い合わせください。24 時間 365 日対応しています。

## まとめ

この演習では、会話型 AI システムを高度なビジネス自動化機能で強化しました。次のことを達成しました:

- **Microsoft Teams と統合された包括的な旅行承認ワークフローを作成しました**。
- **組織のナレッジ ソースとドメイン固有の専門知識を備えた専門的な Leave Manager エージェントを構築しました**。
- **異なる AI エージェント間のシームレスなコラボレーションを可能にするマルチエージェント オーケストレーションを確立しました**。
- **会話開始から Teams 通知およびエージェント間ルーティングまでのエンドツーエンドのビジネス プロセスを実装しました**。

### ラボを正常に完了しました!
