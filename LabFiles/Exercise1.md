# 演習 1: Safe Travels エージェントを作成して Microsoft Teams に展開する

### 推定所要時間: 30 分

## 概要

この基礎演習では、Microsoft Copilot Studio の Safe Travels テンプレートを使用して最初の AI エージェントを作成します。これは実践的なハンズオンの導入であり、Microsoft Teams に展開された動作する旅行アシスタント エージェントが得られます。

Safe Travels エージェントは、従業員の旅行関連の質問、ポリシー情報、およびガイダンスを支援します。テンプレートを使用することで、強力な AI エージェントを簡単に作成できることを実感できます。この演習は、あらゆるビジネス シナリオに適用できるコアなエージェント開発のワークフローに慣れることに重点を置いています。

## 目的

次のタスクを完了します:

- タスク 1: データ テーブルをインポートし、Copilot Studio に移動する
- タスク 2: テンプレートから Safe Travels エージェントを作成する  
- タスク 3: エージェントの機能をテストして検証する
- タスク 4: Microsoft Teams にエージェントを公開して展開する

## タスク 1: データ テーブルのインポートと Copilot Studio への移動

このタスクでは、必要なデータ テーブルを Power Platform 環境にインポートし、エージェントの作成を開始するために Copilot Studio に移動します。

1. Power Apps ポータルに戻り、前に作成した環境に切り替えます。

   ![](../media/papps1.png)

1. 完了したら、左メニューから **Tables (1)** を選択し、**Create with Excel or .CSV file (2)** をクリックします。

   ![](../media/leav-man-e1-g-2.png)

   > **注意:** アクセス権がない旨のメッセージが表示された場合は、**Switch and create** をクリックします。

   ![](../media/saf-tra-cor-v2-g1.png)

   > **注意:** 直接 **Upload an Excel file** 画面に移動した場合は、**Cancel** をクリックして戻ります。

   ![](../media/saf-tra-cor-v2-g2.png)

1. 次のペインで **Select from device** をクリックし、ポップアップ ウィンドウでファイルを選択します。

   ![](../media/ex2img11.png)

1. ファイル ピッカー ダイアログで:
   - **`C:\datasets\Safe-Travels-Agent-Automate`(1)** に移動します。
   - **Leave balance Tracker.xlsx (2)** を選択します。
   - **Open (3)** をクリックしてファイルを追加します。

      ![](../media/cor-g-g1.png)

1. In the **Import an Excel or .CSV file** pane, ensure the table is included, and then click **Import**.

   ![](../media/saf-tra-cor-v2-g3.png)

1. On the table mapping screen, click **Save and exit**.

   ![](../media/saf-tra-cor-v2-g4.png)

1. In the **Done working?** dialog, click **Save and exit**.

   ![](../media/saf-tra-cor-v2-g5.png)

1. After provisioning completes, open **Tables (1)** and confirm the **Employee (2)** table is listed; note the logical **prefix (3)** which uniquely identifies the table for future automation (not used further in this lab).

   ![](../media/ex1-travel-g4.png)

   > **Tip:** If the **Employee** table isn't visible, verify you've switched to **ODL_User <inject key="Deployment ID" enableCopy="false"></inject>'s Environment**.

1. Navigate to **Microsoft Copilot Studio** by opening a new browser tab and using the link below:

   ```
   https://copilotstudio.microsoft.com
   ```

1. On the **Welcome to Microsoft Copilot Studio** screen, keep the default **country/region** selection and click **Get Started** to continue.

   ![](../media/gs-travel-g2.png)

1. If the **Welcome to Copilot Studio!** pop-up appears, click **Skip** to continue to the main dashboard.

   ![](../media/gs-travel-g3.png)

1. In Copilot Studio, open the environment picker **(1)**, expand **Supported environments (2)**, and select **ODL_User <inject key="Deployment ID" enableCopy="false"></inject>'s Environment (3)** to switch.

   ![](../media/ex1-travel-g6.png)

   > If you are not able to see the environment under **Supported environments**, please refresh or log in once again by logging out.

## Task 2: Create Safe Travels & Leave Manager Agents

In this task, you will create two AI agents: the **Safe Travels Agent** to assist with travel-related queries and the **Leave Manager Agent** to manage employee leave information and approvals. This helps you understand how to quickly build and customize multiple agents for different business scenarios.

1. In Copilot Studio, click **Agents (1)** and select the **Safe Travels (2)** template card.

   ![](../media/sfimg1.png)

   > **Note:** If the template isn’t visible, use the search box.
   
1. In the next pane, enter the following details in **Name (1)** and **Description (2)** fields, and then click **Create (3)**.

   | Key | Value |
   |-----|-------|
   | Name | `Safe Travels Agent` |
   | Description | `A travel assistant agent that helps employees with travel planning, policies, and guidance` |

   ![](../media/ex1-travel-g8.png)

1. After clicking **Create**, verify the green success banner **"Your agent has been provisioned."** appears and the **Overview** tab loads.

   ![](../media/saf-tra-cor-v2-g6.png)

   > **Template Benefits:** Safe Travels ships with pre-configured travel flows and knowledge, reducing setup time.

1. On **Overview (1)** click **+ Add knowledge (2)** to begin attaching internal travel policy content.

   ![](../media/ex1-travel-g10.png)

   > **Note:** Adding knowledge sources improves grounded responses; keep policy files updated for accuracy.

1. On the **Add knowledge** screen, click **select to browse** to upload a knowledge file.  

   ![](../media/cor-g-g3.png)

1. In the file picker window, navigate to the folder **C:\datasets\Safe-Travels-Agent-Automate (1)**, select the **Travel Policy (2)** Word document file, and then click **Open (3)**.

   ![](../media/cor-g-g4.png)

1. After the file is uploaded successfully, click **Add to agent** to include the document as a knowledge source for your agent.

      ![](../media/ex1-travel-g11.png)

1. The system will process your agent creation. **Provisioning may take 10–15 minutes, please proceed to the next step while it completes**.

   ![](../media/ex1-travel-g12.png)

   ![](../media/ex1-travel-g13.png)

1. Navigate to **Copilot Studio**, click **Agents (1)** and then select **+ Create a Blank Agent (2)** to create the specialized Leave Manager agent.

   ![](../media/saf-tra-cor-v2-g7.png)

   > **Note:** The Copilot Studio UI may change over time; if prompted for the agent name, enter the following:

   > ```
   > Leave Manager Agent
   > ```

1. Wait till the agent provisioning completes, click on **Edit** to configure the agent details.

      ![](../media/sfimg3.png)

      > **Agent Specialization:** Creating domain-specific agents allows for better accuracy, focused training, and more relevant responses for specific business functions.

1. In the next pane, enter the following details in **Name (1)** and **Description (2)** fields, and then select **Save (3)**.

   | Key | Value |
   |-----|-------|
   | Name | `Leave Manager Agent` |
   | Description | `This agent is to track the leaves of all the employees, their leave balance and leave history to approve or reject any new leave requests.` |

   ![](../media/saf-tra-cor-v2-g10.png)

1. Once saved, scroll down and click on **Edit** on **Instructions** card.

   ![](../media/saf-tra-cor-v2-g11.png)

1. Configure the following instruction and click on **Save** once after adding.

   | Key | Value |
   |-----|-------|
   | Instructions | `Track the leaves of employees. Track their leave balance. Apply/Reject leaves based on their balance.` |

   ![](../media/saf-tra-cor-v2-g12.png)

1. From the **Overview (1)** tab and click **Add knowledge (2)** to include organizational data sources that will enhance your agent's leave management capabilities.

   ![](../media/ex2-travel-g70.png)

1. Click **select to browse** to upload the leave management documentation that will serve as the knowledge foundation for your agent.

   ![](../media/ex2-travel-g71.png)

1. In the file picker window, navigate to the folder **C:\datasets\Safe-Travels-Agent-Automate (1)**, select the files **Leave balance Tracker.xlsx (2)**, and then click **Open (3)**.

   ![](../media/cor-g-g7.png)

1. Upload the required leave policy and tracking files, then click **Add to agent** to integrate them as authoritative knowledge sources.

   ![](../media/saf-tra-cor-v2-g13.png)

1. Verify that all uploaded knowledge sources display **Ready** status, confirming successful integration and availability for agent responses.

   ![](../media/cor-g-g10.png)

   ![](../media/cor-g-g24.png)

   > **Note:** It may take 10–15 minutes for all knowledge sources to show the **Ready** status. You can proceed with the next task while the processing completes.

   > **Knowledge Integration:** Successfully uploaded knowledge sources enable your agent to provide accurate, policy-compliant responses based on your organization's actual leave management data.

1. Please follow the same steps and upload **C:\datasets\Safe-Travels-Agent-Automate\Leave Policy** document.

## Task 3: Test and Validate Agent Functionality

In this task, you'll test your Safe Travels agent to validate its functionality and responses to travel-related queries.

1. From the left navigation menu, click **Agents (1)**, and then select **Safe Travels Agent (2)** from the list to open it.

   ![](../media/saf-tra-cor-v2-g14.png)

1. Verify that the uploaded knowledge source shows the **Ready** status as highlighted.

   ![](../media/ex1-travel-g13.png)

   > **Note:** If the status is not yet **Ready**, you can continue with the next steps. However, the agent's responses may not reflect the latest data until the knowledge source is fully processed.

   > **Note:** It is recommended that you proceed to the next tasks and perform them. Once the knowledge source is fully processed, you can return later to retest the agent for improved and accurate responses during future interactions.

1. Click **Test** to open the test panel and verify your agent’s responses.

   ![](../media/ex1-travel-g14.png)

1. In the test chat, enter the following **prompt (1)** and then select **Send (2)**.

   ```
   How to apply for passport?
   ```

   ![](../media/ex1-travel-g16.png)

1. Verify that the **response** generated by the agent is as expected.
   
   ![](../media/ex1-travel-g17.png)

   > **Note:** The output may vary if the knowledge source (Word file) is still processing. This is expected behavior. You can continue with the next task you’ll be interacting with the agent again in the upcoming tasks once the knowledge source is fully ready.

1. In the test chat, enter the following **prompt (1)** and then select **Send (2)**.

   ```
   What is our company travel policy?
   ```

1. Verify that the **response** generated by the agent is as expected.

   ![](../media/ex1-travel-g18.png)
   
1. Continue testing with additional travel scenarios to ensure the agent responds appropriately to various travel-related questions.

   > **Knowledge Integration:** The agent leverages its built-in travel knowledge to provide helpful responses across various travel scenarios.

## Task 4: Publish and Deploy Agent to Microsoft Teams

In this task, you will publish your Safe Travels agent and deploy it to Microsoft Teams, making it accessible to your organization's employees.

1. After testing, click the **Publish** button in the top-right corner of the agent interface to begin the publishing process.

   ![](../media/ex1-travel-g21.png)

1. In the publish dialog, review the publishing details and click **Publish** to confirm and publish your agent.

   ![](../media/sfimg8.png)

   > **Publishing Process:** The agent will be packaged and made available for channel deployment. This process may take a few moments to complete.

1. Open a new browser tab and navigate to Microsoft Teams using the link below:

   ```
   https://teams.microsoft.com/v2/
   ``` 

1. If prompted to sign in, enter your **email address (1)** and click **Next (2)**.

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

      ![](../media/ex1-travel-g24.png)

1. Enter the **Temporary Access Pass (1)** and click **Sign in (2)**.

   - **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject>

      ![](../media/ex1-travel-g25.png)

1. If you see a "Get to know Teams" welcome screen, click **Get Started** to proceed.

   ![](../media/ex1-travel-g22.png)

1. Once published successfully, navigate to the **Channels** section to configure deployment channels for your agent.

   ![](../media/ex1-travel-g28.png)

1. In the Channels interface, you'll see available deployment options. Select **Microsoft Teams** to deploy your agent to Teams.

   ![](../media/ex1-travel-g29.png)

   > **Channel Benefits:** Deploying to Microsoft Teams provides users access through their familiar collaboration environment, increasing adoption and usage.

1. In the **Teams and Microsoft 365 Copilot** window, select the checkbox **Make agent available in Microsoft 365 Copilot (1)**, and then click **Add channel (2)**.

   ![](../media/ex1-travel-g30.png)

1. Once the channel is added successfully, A dialog to publish will be shown. Please click on **Publish**.

   ![](../media/sfimg8.png)

1. Once published, select the **See agent in Teams** option to add the agent in Teams.

   ![](../media/cor2-gs-g2.png)

1. If prompted to download the Teams desktop app, click **Use the web app instead** to continue using Teams in your browser.

   ![](../media/ex1-travel-g34.png)

1. In the Safe Travels Agent dialog, review the agent information and click **Add** to install the agent in your Teams environment.

   ![](../media/ex1-travel-g35.png)

1. After successful installation, you'll see a confirmation message. Click **Open** to start using your Safe Travels Agent immediately.

   ![](../media/ex1-travel-g36.png)

1. The Safe Travels Agent chat interface will open. Type your first message in the text box (1) and click the **Send** button (2) to test the agent.

   ![](../media/ex1-travel-g39.png)

1. The **Safe Travels Agent** chat interface will open. Type your first message in the text box **(1)** and click the **Send** button **(2)**.

   ![](../media/ex1-travel-g40.png)

1. To start interacting with the agent. Ask a few travel-related questions and review the agent’s responses.

<validation step="93a6c432-2df0-4b2a-bea2-658266d0ac58" />
 
> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help.

## Summary

You've successfully:

- Imported data tables and navigated to Copilot Studio
- Created a working Safe Travels agent using Microsoft's template
- Tested the agent's travel assistance capabilities with real queries
- Published and deployed the agent to Microsoft Teams for your organization

Your Safe Travels agent is now live and ready to help employees with travel questions, passport information, and destination guidance. You've experienced the power of low-code AI development - creating enterprise-ready conversational agents without any programming.

### You have successfully completed Exercise 1. Click **Next >>** to continue to Exercise 2.
