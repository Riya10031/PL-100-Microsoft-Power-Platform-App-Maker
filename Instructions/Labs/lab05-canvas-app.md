# Lab 03.2: Canvas app

In this module you will design and build a canvas app for the company employees to submit problem reports.

## Lab Scenario

  - Import and use a pre-built component library
  - Create a Power Apps canvas app
  - Connect to a data source
  - Filter data
  - Create data rows
  - Use images with data rows
  - Embed canvas Power App into Microsoft Teams

## Lab Objectives

  - Exercise 1: Create canvas application
  - Exercise 2: My reports
  - Exercise 3: Allow removing reports
  - Exercise 4: Add new report
  - Exercise 5: Test the application
  - Exercise 6: Embed canvas app in Microsoft Teams

## Prerequisites

* Must have completed **Lab 02.1: Data model and model-driven app**

## Detailed steps

### Exercise 1: Create canvas application

In this exercise, you will import a solution with shared components, create a view for the Problem Report table and create a canvas application.

#### Task 1: Import component library solution

In this task, you will import the shared components solution into your environment. This shared component library was built by another team at your company.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and select **Import solution**.

    ![A screenshot with an arrow pointing to the import button](03-2/media/image1.png)

3.  Select **Browse**.

4.  Go to the Lab Resources folder, select the **Shared Components** solution file, and select **Open**.

    > **TIP**
    > 
    > The lab resources can be found here: `D:\Instructions\Labs\03-2\Resources\SharedComponents_1_0_0_4.zip`

5.  Select **Next**.

6.  Select **Import** and wait for the import to complete.

7.  Select **Publish all customizations** and wait for the publishing to complete.

8.  Open the **Shared Components** solution.

9.  The solution should have one item in it. (**Lamna Healthcare Shared Components**)

    ![A screenshot of the shared components window with the Lamna Healthcare shared components item](03-2/media/image2.png)

    > **IMPORTANT**
    >
    > There is an issue where importing the app as part of a solution may not add it to your components library. The following steps are designed to resolve the issue.

10. Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.    

11. Select **Apps** and select the **Lamna Healthcare Shared Components App**.

12. Select **Edit** to edit the app.

    ![A Screenshot with an arrow pointing to the edit button](03-2/media/image2-1.png)

13. If prompted, select your **Region/Country** and select **Get started** or select **Skip**.
    
    > **NOTE:** When the app is open in Edit mode, move on to next step, as the Preloader component shows a Loading icon but it is not actually waiting for something to load.

14. After the app opens, select the drop-down &#709; next to the **Save** button and select **Save as**.

15. Change app name to `Lamna Healthcare Shared Components A` and select **Save**.

    ![A screenshot with a border around the app name saved as Lamna Healthcare Shared Components A](03-2/media/image2-2.png)

16. Select **OK** when prompted to save as a new library.

17. Close the **Lamna Healthcare Shared Components** tab in your browser.


#### Task 2: Create view

In this task, create a view that will show the current user’s problem reports. Later this view will be used with the filter function in the canvas app.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Locate and open the **Problem Report** table.

4.  Select **Views** in the tree view in the **Objects** pane and open the **Active Problem Reports** view.

5.  Select **Edit filters**.

    ![A Screenshot with an arrow pointing to the edit filters button](03-2/media/image4.png)

6.  Change the filter to **Created By, Equals current user** and select **Ok**.

    ![A screenshot of the edit filters window](03-2/media/image5.png)

7.  Select **Save As**.

    ![A Screenshot with an arrow pointing to the save as button](03-2/media/image6.png)

8.  Enter `My Reports` for **Name** and select **Save**.

9.  Select **Save and publish** and wait for the publishing to complete.

10. Select the **🡠 Back** button on the command bar to go back to the Problem Report table details.


#### Task 3: Create the user application

In this task, create a canvas app using the phone form factor.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New** > **App** > **Canvas app**.

4.  Enter **Company 311 Phone App**, select **Phone** for format, and select **Create**.

5.  Select **Skip**.

6.  In the **Tree view**, select the three dots menu for **Screen1** and select **Rename**.

7.  Rename the screen to **Main Screen** and press enter. 

    >**Note:** It’s always a good idea to give screens a meaningful name.

    ![A screenshot with the Screen 1 name highlighted and renamed Main Screen](03-2/media/mainscreen.png)

8.  Select the **Main Screen** and then select **+ Insert** from the left navigation pane.

    ![A Screenshot with an arrow pointing to the plus icon for insert](03-2/media/image11.png)

9.  Select **Get more components**.

    ![A screenshot with a border around the get more components button](03-2/media/image12-1.png)

10. Expand the **Lamna Healthcare Shared Components A** Library, select **Header** and **Tab Control** (1), and then select **Import (2)**.

    ![A screenshot of the import components window with Ta control and header selected](03-2/media/header.png)

11. Expand **Library components**, select **Header**. **Header** and **Tab Control** these are both components from the library you imported earlier in the lab.

12. Move the **Tab Control** to the bottom of the screen and the **Header Control** to the top of the screen.

13. Navigate back to the **Tree View**. Select the **Header Control** and change the **Text** value to **"Company 311".**

    ![A screenshot of a border around the expression tab with the text value set to company 311](03-2/media/image13.png)

14. Set the **Height** of the **Header Control** to `75`

    ![Set Height - Header](03-2/media/height.png)

15. In the **Tree view**, right-click on the Main Screen and select **Duplicate screen**.

    ![A screenshot with a border around the duplicate screen button](03-2/media/image14.png)

16. Rename the new screen `New Reports Screen`.

17. Select the **Tree view**, select **App** and change the **OnStart** value to the formula below. This formula will create a new variable named My Tabs and set it to a table of tab items.

    ```javascript
    Set('My Tabs', Table( {
    	Label: "My Reports",
    	Screen: 'Main Screen',
    	Icon: "",
    	SelectedIcon:""
    },
    {
    	Label: "New Report",
    	Screen: 'New Reports Screen',
    	Icon: "",
    	SelectedIcon:""
    }
    ))
    ```

    > **IMPORTANT:** When expressions are copied, the quotes and double quotes are sometimes replaced with their “smart” counterparts which are not valid in formulas. If you copy and paste the expression above, make sure the resulting formula does not contain any errors.

    ![A screenshot of the copied expression into the expression tab](03-2/media/image15.png)

18. Select the **Tab Control_1 (1)** component in the **Main Screen** and change the **Items (2)** value to `'My Tabs'` (3).

    ![A screenshot of the items value set to my tabs for Tab control](03-2/media/image16.png)

19. Change the **SelectedColor** value to `Color.WhiteSmoke`.

20. Select the **Tab Control_2** inside the **New Report Screen** and set the **Items** value to `'My Tabs'`.

21. Change the **SelectedColor** value to `Color.WhiteSmoke`.

22. In the **Tree view**, right-click on **App** and select **Run OnStart**.

    ![A screenshot of the run on start button coming from the ellipsis icon for see more under the app button](03-2/media/image17.png)

23. The tab names should update.

    ![A screenshot of the two tabs you added](03-2/media/image18.png)

24. Select **Save** from the command bar.

    ![A screenshot of the two tabs you added](03-2/media/save.png)

    >**Note:** Do not navigate away from this page.


### Exercise 2: My reports

In this exercise, add a gallery that will show reports created by the current logged in user.

#### Task 1: Add gallery

1.  Select the **Main Screen**, select **Insert (1)** menu, then select **Vertical gallery (2)**.

    ![A screenshot of the app designer with a cursor pointing to the vertical gallery option](03-2/media/verticalgallery.png)

2.  Navigate back to the **Tree View**, rename the new gallery to `My Reports Gallery`.

3.  Resize and reposition **My Reports Gallery**, under properties pane, change the setting **Position, Y** value to `75` and the **Height** value to `1000`. It should look like this:

    ![A screenshot of the my reports gallery selected](03-2/media/image20.png)

4.  Select **My Reports Gallery**, go to the **Properties** pane, and under **Data Source** select **Problem Reports** from the drop-down. If you do not see Problem Reports, select **See all tables** or **Search** for the table.

    ![A screenshot of the my reports gallery window and the properties pane with problem reports selected for data source](03-2/media/image21.png)

5.  Under **View**, select the **My Reports** that you created.

6.  Under **Fields**, select **Edit**.

    ![A Screenshot with an arrow pointing to the edit button](03-2/media/image22.png)

7.  Change Subtitle1 to **statuscode**. This is the **Status Reason** column.

    ![A screenshot of a border around subtitle 1 changed to the correct name](03-2/media/image23.png)

8.  Select **Image 1** control within the **My Reports Gallery**. Set **Image** value to the formula below. This allows images to be displayed correctly when view is used as a source.

    `LookUp('Problem Reports', 'Problem Report' = ThisItem.'Problem Report').Photo`

9.  Select the **Save** icon.

    >**Note:** Do not navigate away from this page.


### Exercise 3: Allow removing reports

In this exercise, allow unassigned reports to be removed. This will allow users to easily remove any reports that were accidentally created.

#### Task 1: Allow remove

1.  Expand the **My Reports Gallery**.

2.  Select the **Icon** inside the **My Reports Gallery**.

    ![A screenshot of the arrow icon inside the my reports gallery](03-2/media/image24.png)

3.  In the **Tree view**, double-click **NextArrow1** and rename it to `Remove Report`.

3.  Change the **Icon** value to **Icon.Trash**.

    ![A screenshot showing icon.trash in the expression tab](03-2/media/icontrash.png)

4.  Change the **Visible** value to the formula below. This formula will hide the icon if the status reason is not New.

    `If(ThisItem.'Status Reason' = 'Status Reason (Problem Reports)'.New, true, false)`

    ![A screenshot of the expression tab with the relevant command pasted in](03-2/media/visible.png)

5.  Make sure you still have the **Remove Report** icon selected. Change the **OnSelect** value to the formula below. This formula will remove item from the data source.

    `Remove('Problem Reports', ThisItem)`

6.  Change the **Tooltip** value to `"Remove this report"`.

7.  Select **Save**. 


### Exercise 4: Add new report

In this exercise, add a form to the canvas app to submit new problem reports.

#### Task 1: Add new report form

1.  Select the **New Reports Screen**, select **Insert (1)**, then select **Edit Form (2)**.

    ![A screenshot of the inset tab and forms button selected](03-2/media/edit-form.png)

2.  Navigate back to the tree view, and rename the form to `New Report Form`.

3.  Select **New Report Form**, go to the **Properties** pane, and select **Problem Report** under **Data source**.

4.  Select **Edit fields**.

    ![A Screenshot with an arrow pointing to the edit fields button](03-2/media/image28.png)

5.  If **Status Reason** Column is there you can remove it.

    ![A Screenshot with an arrow pointing to the ellipses icon for more options and a border around the remove button](03-2/media/image29.png)

6.  If **Created On** Column is there remove it.

7.  If **Location** Column is there remove it.

8.  Select **+ Add field**.

9.  Select **Building**, **Department**, **Details**, and **Photo**, and then select **Add**.

10. Resize and reposition the form, setting the **Position, Y** value to `75` and the **Height** value to `900` 

    >**Note:** It takes most of the page and leave enough room for a button at the bottom.

    ![A screenshot of the form resized and reposition for room at the bottom for a button](03-2/media/image31.png)

11. Select the **New Reports Screen**.

12. Select **Insert** then select **Button1**.

13. Navigate back to the tree view, and rename the button `Submit Report`.

14. Move the button below the form, or set **Position, X** value to `180` and **Y** value to `990`.

15. Change the **Submit Report** button **Text** property to `"Submit"`.

16. Select the **Submit Report** button and change the **OnSelect** value to the formula below. This formula will create a new Row in the Problem Reports table.

    `SubmitForm('New Report Form') `

17. Select the **New Report Form**.

18. Change the **OnSuccess** value to the formula below. This formula will show a notification after the new Row gets created and clear the form when the record creation is successful.

    `Notify("Created new problem report row");NewForm('New Report Form')`

19. Select the **New Reports Screen**.

20. Set the **OnVisible** value to the formula below. This formula will create a new form when the screen becomes visible.

    `NewForm('New Report Form')`

21. Select **Save**.

22. Select **Publish**.

    ![A screenshot of the form resized and reposition for room at the bottom for a button](03-2/media/publish.png)

23. Select **Publish this version** and wait for the publishing to complete.

    >**Note:** Do not navigate away from this page.


### Exercise 5: Test the application

In this exercise, test the canvas application by submitting a problem report.

#### Task 1: Test application

> **Important:** Download any image from the browser, and save it in the C-Drive.

1.  Select the **Main Screen** and select **Preview the app**.

    ![A Screenshot with an arrow pointing to the play icon to preview the app](03-2/media/image32.png)

2.  The application should load, and the list should show all the reports you created.

3.  Select the **New Report** tab.

4.  The **New Report Form** should load. Fill out the form and select the **Photo** Column.

5.  Select an image.

6.  Select **Submit**.

7.  The Row should get created successfully and you should see the success message.

    ![A screen of the success message reading "created new problem report record"](03-2/media/image38.png)

8.  Select the **My Reports** tab.

9.  You should see the new report you created. Select the **Remove Report** button to test the delete.

    ![A Screenshot with an arrow pointing to the trash can icon to delete](03-2/media/image35.png)

10. The Row should be deleted and removed from the list.

    ![A screenshot of the row deleted and removed from the list](03-2/media/3apps.png)

11. **Close** the preview mode.

12. **Close** the app studio by closing the browser tab.


### Exercise 6: Embed canvas app in Microsoft Teams

In this exercise, you will add the Company 311 Phone App that you created earlier, to Microsoft Teams as a way for staff to be able to log issues directly within Teams.

#### Task 1: Setup Company 311 Team

In this task, you will setup a **Microsoft Teams** team for the Lamna Healthcare Company, if you have not done so previously.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com) and sign in with the same credentials you have been using previously.

2.  If it asks, select **Use the web app instead** on the welcome screen.

    ![A screenshot of the Microsoft Teams web browser landing page with a border around the use the web app instead button](03-2/media/image-3-teams.png)

3.  When the Microsoft Teams window opens, dismiss the welcome messages.

4.  Select **Teams**.

    ![A screenshot of the Microsoft Teams web browser landing page with a border around the use the web app instead button](03-2/media/teams.png)

5.  On the bottom left corner, choose **Join or create a team**.

6.  Select **Create a team**.

    ![A screenshot of a border around the join or create a team button and another border around the create a team button](03-2/media/createteam.png)

6.  Select **From scratch**.

7.  Select **Public**.

8.  For the Team name enter **Company 311** and select **Create**.

9.  Select **Skip** adding members to Company 311.

10. Do not navigate away from this page.


#### Task 2: Add canvas app to Teams

1.  Select the **General (1)** channel of the **Company 311** team.

2.  At the top of the page, select the **+ (2)** symbol to add a new tab.

    ![A screenshot of a border around the plus icon to add a new tab](03-2/media/general.png)

4.  Search for `power` and select **Power Apps** from the results.

5.  Select **Add** to add Power Apps to Teams.

6.  Select the **Company 311 Phone App** that you created earlier in this lab. 

    > **IMPORTANT:** If you do not see the app you may need to go back to the app editor and publish the app.

7.  Select **Save**. 

8.  The **Company 311** app should now appear on a tab in Microsoft Teams.

    ![A screenshot of the company 311 app appearing on a tab in Microsoft Teams](03-2/media/apps.png)


