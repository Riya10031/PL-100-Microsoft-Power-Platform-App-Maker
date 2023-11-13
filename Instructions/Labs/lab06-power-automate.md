# Course Introduction

> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)

# Lab 04: Power Automate

In this lab, you will create Power Automate cloud flows to automate various parts of the Company 311 solution.

The following have been identified as requirements you must implement to complete the project: 

  - Escalation, approval, and execution process for urgent maintenance issues 

  - Notify reporting user about the issue status changes 

  - How to use a business rule to implement logic.

## Lab Objectives

In this lab, you will complete the following tasks:

- Exercise 1: Build notify flow
- Exercise 2: Build escalation flow
- Exercise 3: Send approval requests as adaptive card in Microsoft Teams(READ-ONLY)

## Prerequisites

* Must have completed **Lab 02.1: Data model and model-driven app**
* Must have completed **Lab 02.2: Business Process Flows and Business Rules**

## Things to consider before you begin

  - What is the most efficient way to identify urgent maintenance issues and escalate them

## Detailed steps  

### Exercise 1: Build notify flow

In this exercise, you create a flow that will notify the creator of a problem when the status changes.

#### Task 1: Create flow

In this task, you will create a flow that send notification when the status of problem report row changes.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.1).png)

4.  Select **+ New** > **Automation** > **Cloud Flow** > **Automated**.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.2).png)

5. Click on **Get Started** if the pop-up comes up.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.3).png)

7.  Enter `when a row` in the search box, then locate and select the **When a row is added, modified or deleted** action from the **Microsoft Dataverse** connector. 

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.4).png)
    
9.  Select **Create**.

10. Select **Modified** for **Change type**, select **Problem Reports** for **Table name**, **Organization** for **Scope** and expand **Show advanced options**.
  
    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.5).png)

12.  Enter `statuscode` for **Select columns** then select **… Menu** button of the trigger step.

11.  Select **Rename**.

12.  Rename the trigger step `When problem report status changes`

13.  Select **+ New step**.

11. Select **Connectors** tab and then select **Microsoft Dataverse**. Select **Get a row by ID**.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.6).png)

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.7).png)

13. Select **Users** for **Table name**.

14. Select the **Row ID** field, go to the Dynamic pane, search for `created` and select **Created By (Value)** to add it.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.8).png)

16. Select **Show advanced options** on the new step.

17. Enter `internalemailaddress` for **Select columns**.

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.9).png)
    
19. Select the **… Menu** button of the new step and select **Rename**.

20. Rename the step `Get problem creator`

21. Select **+ New step**.

22. Search for `send email` and select **Send an email (V2).**

    ![A screenshot showing dropdown menu to create new automated cloud flow](04/media/pl-100(6.10).png)

24. Select the **To** field and select the **Switch to Advanced Mode** arrows icon. Selecting this button toggles show/hide of the Dynamic content pane.

    ![A Screenshot with an arrow pointing to the switch to advanced mode icon](04/media/pl-100(6.11).png)

25. Select the **Primary Email** field from the **Get problem creator** step.

    ![A Screenshot with an arrow pointing to the switch to advanced mode icon](04/media/pl-100(6.12).png)

27. Enter `Problem report status change notification` for **Subject**.

28. Select the **Body** field.

29. Enter `The status of the problem you reported has changed.` and press the **[ENTER]** key.

30. Enter `Problem Title:` followed by a **[SPACE]**, go to the **Dynamic content** pane, search for `title` and select **Title**.

31. Press the **[ENTER]** key.

32. Enter `Current Status:` followed by a **[SPACE]**, go to the **Dynamic content** pane, select the **Expression** tab, paste the expression below, and select **OK**. This expression will show the label of the Status Reason instead of the value.

    `triggerOutputs()?['body/_statuscode_label']`

    ![A Screenshot with an arrow pointing to the switch to advanced mode icon](04/media/pl-100(6.13).png)
    
34. Select the **… Menu** button of the new step and select **Rename**.

35. Rename the step to `Notify problem creator`(1)
    
37. At the top of the page, change the flow name from **Untitled** to `Notify Problem Creator`

38. Select **Save** (2) and wait for the flow to be saved.

    ![A screenshot of the current flow](04/media/pl-100(6.14).png)

39. Select the **🡠** button to go back to the previous page.


#### Task 2: Test the flow

In this task, you will test the Notify Problem Creator flow.

1.  On the Power Apps maker portal, `https://make.powerapps.com` ensure you are in the correct environment.

2.  Select **Apps**, and then select the **Company 311 Admin** Model-driven application. Select **Play**.

    ![A screenshot of the current flow](04/media/task2(1).png)

4.  Select **+ New**.

5. Enter `Flow test` (1) for **Title**, select **ODL_User <inject key="DeploymentID"></inject>** (2) for **Owner**, select **London Paddington** (3) for **Building**,  and select **Save**.

    ![A screenshot of the current flow](04/media/task2(2).png)

    ![A screenshot of the current flow](04/media/task2(3).png)

7. Go back, click on **Activate** on the top, choose **in progress** for the status reason from the dropdown and select **Activate**.

    ![A screenshot of the current flow](04/media/task2(4).png)

    ![A screenshot of the current flow](04/media/task2(5).png)

9.  Close the application browser window or tab.

10.  You should now be back to the [Power Apps maker portal](https://make.powerapps.com/)

11.  Select **Solutions** and open the **Company 311** solution.

12.  Locate and open the **Notify Problem Creator** Cloud flow.

13. You should see a succeeded flow run in the **28-day run history section**. Open the run.

    ![A Screenshot with an arrow pointing to the start date of the 28-day run history section](04/media/task2.png)

14. All the flow steps should have a **green** check mark.

15. Select the **App launcher** and under **Apps**, select **Outlook**.

    ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/task2(6).png)

16. You should have received an email from the Cloud flow. **Open** the email.

17. The email should look like the image below.

    ![A screenshot of the email you should receive with the status of the problem, problem title, and its current status](04/media/task2(7).png)


### Exercise 2: Build escalation flow

In this exercise, you will create and add two new columns to the Problem Report table and create an escalation flow.

#### Task 1: Add Columns

In this task, you add a new Columns to the Problem Report table.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Locate and open the **Problem Report** table in the **Objects** pane.

       ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/task1.png)

5.  Select **+ New > Column**.

       ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/task1(2).png)

7.  Enter **Estimated Cost** for **Display name**, select **Currency** for **Data type** and select **Save**.

       ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/task1(3).png)

9.  Select **Forms** from the **Objects** pane.

10.  Open the **Information** form of type **Main**.

      ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/task1(4).png)

12. Add **Estimated Cost** column to the form and place it below the **owner** column.

13. Add the **Assign to** column and place it below the **Estimated Cost** column.

      ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/TASK1(5).png)

15. The **Resolution details** section of the form should now look like the image below. Select **Save and publish**.

16. Select the **← Back** button located on the top left of the screen.

17. Select **All**, select **Publish all customizations**, and wait for the publishing to complete.

     ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/task1(6).png)


#### Task 2: Build escalation flow

In this task, you will create the escalation flow.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New > Automation > Cloud Flow > Automated**.

4.  Search for **when a row is added** and select **When a row is added, modified, or deleted**  from **Microsoft Dataverse** connector then select **Create**.

5.  Select **Added or Modified** for **Change type**, select **Problem Reports** for **Table name**, select **Organization** for **Scope** and select **Show advanced options**.

7.  Enter **lh_estimatedcost,lh_assignto** for **Select columns**.

     ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/ex-2t2(1).png)

9.  Select the **… Menu** button of the trigger step and select **Rename**.

10.  Rename the trigger step **When a problem report is created or updated**.

11.  Select **+ New step**.

12. Search for **Condition** and Select **Condition** control.

    ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/ex-2t2(2).png)

14. Select the first **Choose a value** field.

15. Go to the Dynamic content pane, search for **estimated** and select **Estimated Cost**.

16. Select **is greater than** in the second field and enter **1000** in the third field.

    ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/ex-2t2(3).png)

18. Rename the condition step to **Check if cost is greater than 1000**.

19. Go to the **If yes** branch and select **Add an action**.

20. Search for **Get a row** and select **Get a row by ID** from **Microsoft Dataverse**.

21. Select **Users** for **Table name**.

22. Select the **Row ID** field and select **Assign to (Value)** from the **Dynamic content** pane.

23. Select **Show advanced options**.

24. Enter **internalemailaddress** for **Select columns**.

    ![A Screenshot with an arrow pointing to the app launcher and a border around outlook](04/media/ex-2t2(4).png)

26. Rename the **Get a Row by ID** step **Get user**.

27. Select **Add an action**.

28. Search for **approval** and select **Start and wait for an approval**.

29. Select **Approve/Reject - Everyone must approve** for **Approval type**.

30. Enter **Cost approval required** for **Title**.

31. Select the **Assigned to** field.

32. Go to the **Dynamic content** pane and select **Primary Email** from the **Get user** step.

33. Paste the markdown text below in the **Details** field.

    > \#\# URGENT Approval Required
    >
    > This is \*\*very\*\* expensive item with the estimated cost of

34. Place your cursor after cost of, go to the Dynamic content pane, select the **Expression** tab, paste the expression below, and select **OK**.

    `formatNumber(triggerOutputs()?['body/lh_estimatedcost'], 'C2')`

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-2t2(5).png)

35. Select **Add an action**.

36. Search for **condition** and select the **Condition** action from the Control connector.

37. Select the first **Choose a value** field.

38. Go to the **Dynamic content** pane, search for **Outcome** and select **Outcome**.

39. Select **equals to** in the second field and enter **Reject** for value in the third field.

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-2t2(6).png)

41. Go to the **If yes** branch and select **Add an action**.

42. Search for **update a Row** and select **Update a Row** from **Microsoft Dataverse**.

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-2t2(7).png)

44. Select **Problem Reports** for **Table name**.

45. Select the **Row ID** field.

46. Go to the **Dynamic content** pane, search for **problem report** and select **Problem Report**.

47. Select **Show advanced options**.

48. Select the **Resolution** field, go to the **Dynamic content** pane and select **Response summary**.

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-2t2(8).png)

50. Select **Won’t fix** for **Status Reason**.

51. Rename the step **Update problem report**.

52. Scroll up and rename the flow **Escalate Expense Approval**.

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-2t2(9).png)

54. Select **Save**.
    
55. Close the flow designer browser window or tab.

56. Select **Done** on the popup.


#### Task 3: Test flow

In this task, you will test the escalation flow.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps** and open the **Company 311 Admin** application.

3.  Open one of the **Problem Report** rows.

4.  Scroll down, enter **2700** for **Estimated Cost**, assign it to **yourself** (for test purposes) and select **Save**.

      ![A Screenshot with an arrow pointing to the cost approval required request](04/media/ex2-t3(1).png)

6.  Navigate to the [Power Automate maker portal](https://make.powerautomate.com/).

7.  Select **Approvals**.

8.  You should see at least one approval in the received tab. Open the approval. It can take around 10-15 minutes for approvals to show up here on the first run.

    ![A Screenshot with an arrow pointing to the cost approval required request](04/media/ex2-t3(2).png)

9.  Select **Reject**, enter **We don't have the funds for this item** (optional) for **comment**, and select **Confirm**.

    ![A Screenshot with an arrow pointing to the cost approval required request](04/media/ex2-t3(3).png)

10.  Go back to the **Company 311 Admin** application.

11. Change the view to **My Reports** and open the same row you change the estimated cost.

12. The **Status Reason** should be set to **Won’t fix** and the **Resolution** should contain the details of Approver, Response, Request Date and Response Date.

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/TASK2.2.png)

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/TASK2.1.png)

14. Select **Save**, if you have not done so previously.

# READ-ONLY

### Exercise 3: Send approval requests as adaptive card in Microsoft Teams

In this exercise, you will setup a team in Microsoft Teams dedicated to the Company 311 applications. You will modify the flow to send the approval request as an adaptive card in Teams chat instead of an approval message.

* Task 1: Setup Company 311 Team
* Task 2: Modify flow to send adaptive card in Teams chat
* Task 3: Test adaptive card

#### Task 1: Setup Company 311 Team

In this task you will setup a Microsoft Teams team for the Lamna Healthcare Company, if you have not done so in previous exercises.

**Note:** If you have already created the **Company 311** Teams in the Microsoft teams, skip this part and continue to the next task.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com) and sign in with the same credentials you have been using previously.

2.  Select **Use the web app instead** on the welcome screen.

    ![A screenshot of the Microsoft Teams landing page with a border around the use the web app instead button](04/media/ex-3.png)

3.  When the Microsoft Teams window opens, dismiss the welcome messages.

4.  On the top left corner, clcik on **"+"** and Select **Create a team** .

    ![A screenshot with a box around the join or create a team button at the bottom of the window and a border around the create a team button](04/media/ex-3t1(1).png)

6.  Press **From scratch**.

       ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-3t1(2).png)
   
8.  Select **Public**.

9.  For the Team name choose **Company 311** and select **Create**.

10.  Select **Skip** adding members to Company 311.


#### Task 2: Modify flow to send adaptive card in Teams chat

In this task you will replace the approval sent by email with an adaptive card. 

1.  Navigate to the [Power Automate maker portal](https://make.powerautomate.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **Cloud flows** from the **Objects** pane and open the **Escalate Expense Approval** flow. Select **Edit**. 

4.  Locate **Start and wait for an approval** step created earlier in **Exercise 2, Task 2**. 

5.  Select the **...** menu, and then select **Delete**. 

     ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-3t2(1).png)
    
6.  Hover your mouse between the steps, select the **+** to insert a new step then select **Add an action**. 

7.  Search for **approval**, and select **Create an approval**. 

    ![A Screenshot with an arrow pointing to the ok button in the expression tab under the pasted expression](04/media/ex-3t2(2).png)
  
8.  Select **Approve/Reject - Everyone must approve** for **Approval type**. 

9.  Enter **Cost approval required** for **Title**. 

10. Select the **Assigned to** field. 

11. Go to the **Dynamic content** pane and select **Primary Email** from the **Get user** step. 

12. Paste the markdown text below in the **Details** field. 

    > \*\*{title}\*\*
    >
    > {details}
    >
    > This is a \_very\_ expensive item with the estimated cost of

13. Select **{title}** placeholder, go to the **Dynamic content** pane, locate and select **Title** field from **When a problem report is created or updated** step.

14. Select **{details}** placeholder, go to the **Dynamic content** pane, locate and select **Details** field from **When a problem report is created or updated** step.

15. Place your cursor after **cost of** , go to the **Dynamic content** pane, select the **Expression** tab, paste the expression below, and select **OK**.

    `formatNumber(triggerOutputs()?['body/lh_estimatedcost'], 'C2')`

16. Your step should look like the following: 

    ![A screenshot of the create an approval window with the following. Approval type as approve/reject - everyone must approve, title as cost approval required, assigned to primary email, details as title, details, some text and format number, item link, and item link description](04/media/ex-3t2(3).png)

17. Hover your mouse again below Create an approval step, select **+** and then select **Add an action**.

18. Search for `teams` and select **Post adaptive card and wait for a response** action.

19. Select **Flow bot** for Post as and select **Chat with Flow bot** for Post in.

20. Select the **Recipient** field.

21. Go to the **Dynamic content** pane and select **Primary Email** from the **Get user** step.

22. Select **Message** field.

23. Go to the **Dynamic content** pane and select **Teams Adaptive Card** from the **Create an approval** step.

24. The **Post adaptive card and wait for a response** step should look like the image below

25. Hover your mouse again below Post card in a chat or channel step, select **+** and then select **Add an action**.

26. Search for `approval` and select **Wait for an approval** action.

27. Select **Approval ID** field.

28. Go to the **Dynamic content** pane and select **Approval ID** from the **Create an approval** step.

29. You now have replaced **Start and wait for an approval** step with the following:

30. Expand the **Condition** step. The left side of the condition should be empty because it was referring the step which is now removed. 

31. Go to the **Dynamic content** pane, search for `outcome`, and select **Outcome** from **Wait for an approval** step. 

32. Locate **Update problem report** step under **If yes** branch. 

33. Select **Show advanced options**.

34. Select the **Resolution** field, go to the **Dynamic content** pane, and select **Response summary** from **Wait for an approval** step.

35. Select **Save**.

36. **Close** the flow designer browser window or tab.

37. Select **Done** on the pop-up.


#### Task 3: Test flow

In this task, you will test the escalation flow with the Teams and adaptive cards.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps** and open the **Company 311 Admin** application.

3.  Open one of the **Problem Report** Rows.

4.  Scroll down, enter any amount greater than **1000** for **Estimated Cost**, assign it to **yourself** (for test purposes) and select **Save**.

5.  Navigate to [Microsoft Teams](https://teams.microsoft.com).

6.  Select **Chat**.

7. You should see the **Cost approval required** adaptive card in a message from **Power Automate**.

8. Select the **Reject** button and enter a comment of your choice in the **Comments** area, for example **The item is too expensive**.

9. Select **Submit**. The card will become read-only.

10. Go back to the **Company 311 Admin** application.

11. Change the view to **My Reports** and open the same Row you change the estimated cost.

12. The **Status Reason** should be set to **Won’t fix** and the **Resolution** should contain the details of Approver, Response, Request Date and Response Date.


## **Discussion**

  - Would creating a boolean field for Approved/Rejected be better?
  - What are the pros and cons of using Microsoft Teams over regular email?

## **Bonus exercises**

  - Add ability for the users to subscribe to the reported problems and only notify if there is a subscription. 
  - Auto-subscribe creator of the problem report.
  - How to find out previous value of status reason?
  - Create your own adaptive card using [Adaptive Cards Designer](https://adaptivecards.io/designer/).
