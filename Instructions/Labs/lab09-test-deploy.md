# Course Introduction

> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)

# Lab 07: Test & Deploy

In this lab you will complete solution configuration by adding security roles for the users. Then you will verify, test, and deploy the solution in the production environment.

## Lab Objectives
In this lab, you will complete the following tasks:

- Exercise 1: Create security roles for users 
- Exercise 2: Run solution checker
- Exercise 3: Use Test Studio to create test case for submitting problem (ok to not include image)
- Exercise 4: Export and import solution
- Exercise 5: Add existing flow to solution

## Prerequisites

* Must have completed **Lab 02.1: Data model and model-driven app**

## Detailed steps

### Exercise 1: Create security roles

In this exercise, you will create security roles for users.

#### Task 1: Create security roles

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution. 

3.  Select **+ New > Security** and select **Security Role**. 

4.  Enter **Company 311 User** for **Role Name** and select the **Custom Entities** tab.

5.  Set the read privilege of the **Building** table to **Organization**.

6.  Set the read privilege of the **Problem Report** table to **User**.

7.  The read privileges for the **Building** and **Problem Report** Tables should now look like the image below. Select **Save Create New**.

   	![A Screenshot with an arrow pointing to the save create new icon in the topmost part of the window and borders around the building and problem report on the list of custom entities](07/media/lab-07(1).png)

8.  Enter **Company 311 Admin** for **Role Name** and select the **Custom Entities** tab.

9. Set all privileges of the **Building**, **Department**, and **Problem Reports** tables to **Organization**.

   ![A screenshot of building, department, and problem report having all privileges selected in the custom entities tab](07/media/lab-07(2).png)

10. Select the **Customization** tab.

11. Set all privileges for **Model-driven app**.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(7).png)

12. Select **Save and Close**.

13. Select **Done** on the pop-up.

14. Select **All** from the **Objects** pane.

15. Select **Publish all customizations** and wait for the publishing to complete.


### Exercise 2: Solution checker

In this exercise, you will run the solution checker on the Company 311 solution.

#### Task 1: Run solutions checker

1.  Make sure you are still on the [Power Apps maker portal](https://make.powerapps.com/) site and you are in the correct environment.

2.  Select **Solutions**, select the **Company 311** solution row, select **Solution checker** and select **Run**. 

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(3).png)

3.  The solution checker should start checking your solution, **wait** for it to complete. The **Solution check** column value will change to **Results** with a timestamp.

4.  **Refresh** the page and select the solution again, select **Solution checker**, and select **View results**.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(4).png)

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(10).png)

6.  Review the issues listed on the **Solution checker results**.

    > **NOTE**
    >
    > If you are seeing errors in the Solution Check Result, open the component showing errors one by one and resolve the issues.
    >
    > At this point you will see errors for the Canvas App. Open the app and fix the Accessible Label and Tab Index errors. For assistance, you can refer to [Microsoft Documentation](https://docs.microsoft.com/powerapps/maker/canvas-apps/accessibility-checker). After resolving the issues, save and publish your app. Go back to the **Company 311** Solution and re-run the solution checker.
    >
    > Users who have vision, hearing, or other impairments can use your canvas app more easily and successfully if you consider accessibility as you design how the app looks and behaves. 


### Exercise 3: Use test studio

In this exercise, you use test studio to create test case for submitting a problem report.

#### Task 1: Create test case

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps**, select the **Company 311 Phone** application, and select **Edit**. Select **Skip** if prompted.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(5).png)

3.  Select **Settings**.

4.  Select **Upcoming features**.

5.  Select the **Preview** tab and enable **Formula level error management** if not already enabled.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(11).png)

7.  **Close** the settings pane.
    
    > **NOTE**
    >
	> Currently test studio cannot record steps inside components like the tab control we are using, you edit the App StartScreen formula, so the app navigates directly to the new report screen.

8.  Select the **Tree view** menu.

9.  Select **App** and select **StartScreen**.

10. Add the formula below.

    ```'New Reports Screen'```
   
    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(6).png)
    
9.  Select **Save**.

10. Select **Publish**.

11. Select **Publish this version** and wait for the publishing to complete.

12. Select the **back** button to go back to the app designer.

13. Select the **Advanced tools** tab and select **Open tests**.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(8).png)

14. Select the **ellipsis** of the **Case** and select **Rename**.

15. Rename the **Case** to `Submit problem report`.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(12).png)

17. Select **Record**.

18. You should see the **New Report** tab.

19. Fill out the form and select **Submit**.

20. Select **Done** button on the bottom-left side of the screen.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(13).png)

22. You should see list of the recorded steps. Select **Play**.

    ![A screenshot of the security role edit dialog with all privileges selected for Model Driven app table](07/media/lab-07(9).png)

23. Select **Publish** and wait for the publishing to complete.

24. The steps should replay correctly. Select **Done**.

25. Close the test studio browser window or tab.

26. Close the app designer browser window or tab.

# READ-ONLY

### Exercise 4: Import export

In this exercise, you will export the company 311 solution and import it into a new environment.

#### Task 1: Export solution

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions**, and open the **Company 311** solution.

3.  Select **+ Add existing**, select **More**, then select **Connection Reference**.

    ![A screenshot of the expanded Add existing menu with add connection reference menu item selected](07/media/add_connection_ref.png)

4.  Select all of the connection references and select **Add**.

5.  Select **Publish all customizations** and wait for the publishing to complete.

6.  Navigate back to the **Solutions** list. 

6.  Select the **Company 311** solution and select **Export Solution** from the toolbar.

    ![A Screenshot with cursor pointing to the Export Solution button](07/media/image8.png)

7.  Select **Next**.

8.  Select **Managed** and select **Export**. Wait for the solution to be packaged and exported.

9.  When it has exported successfully, select **Download** to save the solution to your computer. 

10. Select **Export solution** again. 

11. Select **Next**. 

12. Select **Unmanaged**, change the **version** to match the managed solution version and select **Export**. 

13. You should have the **Managed** and **Unmanaged** versions of the solution exported and downloaded.


#### Task 2: Create new environment and import solution

1.  Navigate to `https://powerapps.microsoft.com/communityplan/`

2.  Select **Existing User? Add a dev environment**. 

3.  Enter your credentials when prompt to sign in.

4.  Select your country from the dropdown menu and select **Accept**.

5.  Navigate to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments) to see a new environment had been created by the system. We will refer to it as the "Prod" environment for the rest of this course (the environment name will be <your account name>'s Environment).

6.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and select the environment you just created.

7.  Select **Solutions** and select **Import solution**.

8.  Select **Browse**.

9.  Select the managed solution you exported and select **Open**.

    ![A screenshot of a border around a zip file of the managed solution you exported](07/media/image10.png)

10. Select **Next**. 

11. Select **Next** again. 

12. Select **Select connection** for outlook and then select **+ New connection**.

    ![A Screenshot with an arrow pointing to the drop down icon and a border around the plus new connection button](07/media/new_connection.png)

13. It will open a new window. Select **Create**.

14. Provide your **credentials**.

15. Close the connections browser window or tab.

16. Select **Refresh**.

17. Repeat steps 12 - 16 for the rest of the of the connections.

18. Select **Import** and wait for the import to complete.

19. Select **Publish all customizations** and wait for the publishing to complete.

20. Open the **Company 311** solution you just imported.

21. Review the components in solution.

22. Select **Apps** and make sure you have both the Canvas and Model-driven applications.

23. Open the **Company 311 Admin** application.

24. The application should load without issues.

25. Close the Company 311 Admin application browser window or tab.

26. Open the **Company 311 Phone** application.

27. The application should load without issues.

28. Close the **Company 311 Phone App** browser window or tab.


### Exercise 5: Add existing flow to solution

An employee has created a simple personal productivity flow. The flow looks like a very useful addition to everyone at the company so the decision was made to make this flow available to everyone by including it into the existing solution.
In this exercise, you will create the flow outside of the solution and then add it to the Company 311 solution.

#### Task 1: Create the team

In this task, you will create the Lunchtime Sports team.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com/).

2.  Select **Teams** and select **Join or create a team**.

    ![A Screenshot with an arrow pointing to the join or create a team button](07/media/join_create_team.png)

3.  Select **Create team**.

4.  Select **From scratch**.

5.  Select **Public**.

6.  Enter `Lunchtime Sports` for **Team name** and select **Create**.

7.  Select **Skip**. 


#### Task 2: Create the flow

In this task, you create a flow that will get triggered when someone is added to the group "Lunchtime Sports", the flow will send a notification to you and tell you to find out what sport the new member will be playing.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment (your practice environment). 

2.  Select **Flows**. 

3.  Select **+ New flow \> Automated cloud flow**. 

    ![A Screenshot with an arrow pointing to the new flow button](07/media/image11.png)

4.  Select **Skip**. 

5.  Search for `groups` and select the **When a group member is added or removed** trigger from the **Office 365 Groups** connector. 

    ![A screenshot with a border around the when a group member is added is added or removed button](07/media/image12.png)

8.  Select **Lunchtime Sports** for Group Id and select **+ New step**. 

9.  Select the **Condition** action from the **Control** connector. 

10. Select the first **Choose a value** field and select **@removed** from the **Dynamic content** pane. 

11. Select **is equal to** for the second value field, and for the third value field select the **Expression** tab, enter `null` and select **OK**. 

    ![A screenshot of a border around the choose value field, then another border around the text null typed into the expression tab and an arrow pointing to the ok button](07/media/image13.png)

12. Go to the **If yes** branch and select **Add an action**. 

13. Search for `get user profile` and select the **Get user profile (V2)** action from the **Office 365 Users** connector. 

14. Select the **User (UPN)** field and select **User Id** from the Dynamic content pane. 

    ![A screenshot of a border around user UPN field and user Id in the field. There is also an arrow pointing to the user Id option in the dynamic content pane](07/media/image14.png)

15. Select **Add an action** again. 

16. Search for `send` and select the **Send me an email notification** action from the **Notifications** connector. 

17. Enter `New Lunchtime Sports Member` for Subject.

18. Select the **Body** field and select **Display Name** from the dynamic content pane.

19. Enter `was added to the Lunchtime Sports team, find out what sports this member is interested in.` after the **Display Name**.

    ![A screenshot of the send me an email notification command in the flow with the relevant text in the subject and body field](07/media/image15.png)

20. Rename the flow `Notify me when a member is added to the Lunchtime Sports group` and select **Save**. 

    ![A screenshot with a box around new name of the flow and an arrow pointing to the save button](07/media/image16.png)


#### Task 3: Test the flow

In this task, you will test the flow. 

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com/). 

2.  Select the **... More options** button of the Lunchtime Sports team and select **Manage team**. 

    ![A Screenshot with an arrow pointing to the ellipsis icon for more options and a border around the manage team button](07/media/image17.png)

3.  Select **Add member**.

4.  Search and select a user you want to use for testing.

5.  Select **Add**.

6.  Select **Close**.

7.  Navigate to [Outlook Online](https://outlook.office.com/). 

8.  After a few minutes, you should receive the email notification. Open the email. 

9.  The email should look like the image below. 

    ![A screenshot of how the email should look](07/media/image18.png)


#### Task 4: Add flow to solution

In this task, you will add the flow to the Company 311 solution.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solutions. 

3.  Select **+ Add existing >> Automation >> Cloud flow**.

4.  Select the **Outside Dataverse** tab, select the flow you created, and select **Add**.

    ![A screenshot of the flow you created selected and an add button below](07/media/image19.png)

5.  Select **Publish all customizations** and wait for the publishing to complete.

6.  Select **Export**.

7.  Select **Next**.

8.  Select **Managed** and select **Export**.

9.  Wait for the export to complete and save the exported solution on your machine.

10. Select **Export** again.

11. Select **Next**.

12. Select **Unmanaged**, change the **version** to match the managed solution you just exported and select **Export**.

13. Wait for the export to complete and save the exported solution on your machine.


#### Task 5: Import solution

In this task, you will import the solution into another environment. 

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and select the **Prod** environment that you created in **Exercise 4 Task 2**. 

2.  Select **Solutions** and select **Import**. 

3.  Select **Browse**. 

4.  Select the **managed** version you just exported and select **Open**.

5.  Select **Next**.

6.  You should get a message **This solution package contains an update for a solution that is already installed**, select **Import**.

    ![A screenshot of the import a solution pane with the message mentioned in step six having appeared.](07/media/image27.png)

7.  Wait for the solution import to complete.

8. Open the **Company 311** solution. 

9. Locate the flow you added to the solution and open it.

    ![A Screenshot with an arrow pointing to the name of the flow you added to the solution](07/media/image21.png)

10. Select **Edit**.

    ![A Screenshot with an arrow pointing to the edit button](07/media/image22.png)

11. Expand the trigger.

12. Select **+ Add new connection**.

    ![A Screenshot with an arrow pointing to the add new connection button](07/media/image23.png)

13. Expand the condition.

14. Expand the first step in the **If yes** branch.

15. Select **+ Add new connection** again.

16. Expand the last step. 

17. Select **+ Add new connection** one more time.

18. Select **Save** and wait for the flow to be saved.

19. Select the **<-** back button.

20. Select **Turn on**.

21. The flow should show the status as **On**. You can verify the Status value in the Details sections.

