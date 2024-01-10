# Course Introduction
 
> -  Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)

# Lab 03.1: Create apps in Teams

## Lab Scenario

It is not uncommon for organizations to accumulate unused computer peripherals, power cords and other electronics. Your organization is taking steps to reuse existing devices and computer peripherals before ordering new equipment.

You are asked to create an application where users can post devices they no longer need and browse through what their colleagues posted.

## Lab Objectives

Through this lab, you will be able to complete and gain insights into the following exercises:
 
-  Exercise 1: Get started with Microsoft Dataverse for Teams
-  Exercise 2: Create application
-  Exercise 3: Test and publish application

## Requirements

1)	Application must use Dataverse for Teams.
2)	Users should be able to create new items, edit items they created and see items created by other users.
3)	Items should be removed from the list if they are no longer available.
4) Allow users to reserve an item.
5) Allow user to mark item for pick up.
6) If item is reserved, only reserved user should be able to mark item picked up.
7) Users should be able to search items.

## Exercise 1: Get started with Microsoft Dataverse for Teams

In this exercise, you will create a new team and install Power Apps for Teams.

### Task 1: Create team

In this task you will create a new team.

1.  In the browser, open an another tab, and in the browser search for **[Microsoft Teams](https://teams.microsoft.com).

    >**Note:** If it opens the Microsoft teams page, select **Get Started**. 

    ![A screenshot with a box around the teams button on the left side of the window and an arrow pointing to the create team button](06/media/getstarted.png)

    >**Note:** If it asks for the sign in credentials, then enter the username:- <inject key="AzureAdUserEmail"></inject>, and password:- <inject key="AzureAdUserPassword"></inject>

    >**Note:** If it shows **Welcome to Microsoft Teams!** page, select **Get Started**.

1. On **Stay signed in to all your apps** page, select **No, sign in to this app only**.

    >**Note:** If prompted **One more step to set up Teams with Office** select **Let's do it**, and close the slides.

    >**Note:** If it asks to **Get the Windows app** or **Use the web app instead**, select **Use the web app instead**.

1. Select **Teams** from the lef-hand navigation menu.

1.  Select the **Create a new team** button.

3.  Select **From scratch**.

4.  Select **Public**.

5.  Enter **Green (1)** for **Team name** and select **Create (2)**.

    ![A screenshot with the word green in the team name field](06/media/teamsgreen.png)

6.  Select **Skip** on the **Add members to Green** screen.

7.  You should now have a new team named **Green**.

    ![A screenshot of the microsoft teams page with your new team named green now under your teams](03-1/media/ex1-t1-image3.png)

8.  Do not navigate away from this page.


### Task 2: Install Power Apps

In this task you will install Power Apps for Teams.

1.  Select the **ellipsis More added apps (1)**, search for power apps and select **Power Apps (2)**. 

    ![A Screenshot with an arrow pointing to the ellipsis icon for more added apps on the left side of the page and a box around power apps button](06/media/ellipses.png)

3.  Right-click on the Power Apps tab and select **Pin**. 

    ![A Screenshot with an arrow pointing to the power apps icon and a box around the pin button](06/media/powerapps-1.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

## Exercise 2: Create application
In this exercise, you will provision Dataverse for Teams by creating an application and you will also create a Dataverse table with columns.

### Task 1: Create application

In this task, you will provision Dataverse for Teams by creating an application.

1.  Navigate to Desktop and search for Microsoft teams and select it. Select **Keep using the new teams**.

2.  Select **Power Apps (1)** and select **Start now (2)**.

    ![A screenshot of the power apps for teams home page](06/media/powerapps-2.png)

3.  Select the **Green (1)** team you created and select **Create (2)**.

    ![A screenshot of the power apps for teams home page](06/media/greencreate.png)

    >**Note:** You have to **wait** until provisioning is complete.

5.  Enter **Upcycle (1)** for App name and select **Save (2)**.

    ![A screenshot of the power apps for teams home page](06/media/upcycle.png)

6.  Do not navigate away from this page.


### Task 2: Create table
In this task, you will create a table and columns.

1.  Select **With data (1)** and then select **Create new table (2)**.

    ![A screenshot with data option selected and cursor pointing to the create new table link from the select a data source prompt](03-1/media/lab4-ex1-t1-19.png)

2.  Select **Start with a blank table** in Create new table tab.

    ![A screenshot with data option selected and cursor pointing to the create new table link from the select a data source prompt](03-1/media/lab4-ex1-t1-20.png)

3.  Click on **Edit (1)** and Enter **Gadget (2)** for **Display name** and select **Save (3)** then select  **Save and close**.

    ![A screenshot with data option selected and cursor pointing to the create new table link from the select a data source prompt](06/media/newtable.png)

4. Select **Data (1)** tab then select **ellipse (2)** of Gadgets table and select **Edit data (3)**.

    ![A screenshot with data option selected and cursor pointing to the create new table link from the select a data source prompt](06/media/editdata.png)

6.  Select the **dropdown of New column (1)** and select **edit column (2)**.

    ![A screenshot with data option selected and cursor pointing to the create new table link from the select a data source prompt](03-1/media/2023-11-07_14-24-57.png)

7. Enter **Name (1)** for **Display name** and then select **Save (2)**.

    ![A screenshot with data option selected and cursor pointing to the create new table link from the select a data source prompt](06/media/displayname.png)

7.  Select **+ New column**.

8.  Enter **Description** for **Display name**, select **Text** for **Data type** (displayed as **Single line of text**), and expand the **Advanced options** section.
    Change the **Maximum character count** to `500` and select **Save**.

    ![A screenshot with the cursor pointing to the advanced options link](03-1/media/2023-11-07_14-26-52.png)

9.  Select **+ New column** again.

10.  Enter **Availability** for **Display name**, select **Choice > Choice** for Data Type, and select **+ New choice** under **Sync this choice with** drop-down box. That will open a window to create a global choice to sync with.

11.  Enter **Availability** for **Display name**.

12.  Enter **Available** for the first choice and select **+ New choice**.

13. Enter **Reserved** for the second choice and select **+ New choice**.

14. Enter **Picked up** for the third choice and select **Save**.

    ![A screenshot of the new global choice with 3 choice values entered](03-1/media/2023-11-07_14-27-35.png)

    ![A screenshot of the new global choice with 3 choice values entered](04/media/lab033.png)

15. Select **Availability** in **Sync this choice with**.

16. Select **Available** for **Default choice** and select **Save**.

17. Select **+ New column** menu.

18. Enter **Location** for **Display name**, select **Text** for **Data type** (displayed as **Single line of text**), select **Business required** for **Required** and select **Save**.

    ![A screenshot of the add column window with the relevant text in each field](03-1/media/L3E2T2S18.png)

19. Select **+ New column**.

20. Enter **Photo** for **Display name**, select **File > Image** for **Data type**, check the **Primary image** checkbox and select **Save**.

    ![A screenshot of the add column window with the relevant text in each field](03-1/media/L3E2T2S20.png)

21. Select **+ New column**.

22. Enter **Reserved by** for **Display name**, select **Lookup** for Data type, select **User** for **Related table** and select **Save**.

    ![A screenshot of the add column window with the relevant text in each field](03-1/media/lab4-ex1-t1-27.png)

23. Your table screen should now look like the image below.

    ![A screenshot of the new Gadget table with all columns in a grid layout](03-1/media/lab4-ex1-t1-28.png)

24. Close the table editor by selecting **Close**.

### Task 3: Edit the application

In this task, you will edit the application by filters for gadgets that are available and edit the form.

> **Note:** If you don't have Power Apps Studio open from last step, navigate to **Power Apps app**, select the **Home** tab and open the **Upcycle** application you created. 

1.  Select **Screen1**. If the screen already contains the form, move to the next step, otherwise select **With data** and select **Gadgets** table under **Current environment**. That will create the screen elements including the form.

2.  Make sure **RightContainer1 (1)** is expanded and select the **EditForm1 (2)** control from tree view.

    ![A screenshot with a border around the edit form button under screen 1](03-1/media/lab4-ex1-t1-30.png)

3.  Go to the **Properties** pane and select **Edit fields**.

    ![A Screenshot with an arrow pointing to the edit fields button](03-1/media/ex2-t4-image2.png)

4.  Select the **+ Add field** button.

5.  If any of the fields below do not exist on the EditForm control, select the **+ Add field** button, select the missing field and select **Add**.
    - **Name**
    - **Description**
    - **Availability**
    - **Location**
    - **Reserved by**
    - **Photo**

        ![A screenshot of the add field window](03-1/media/ex2-t4-image3.png)

6.  Remove any extra fields and close the **Fields** pane. Your form should only have **Name, Description, Availability, Location, Reserved By and Photo** columns.

7.  Change **Columns** to **1**.

    ![A screenshot with a border around the columns field and the value of 1 in the field itself](03-1/media/ex2-t4-image4.png)

8.  Select the **Photo_DataCard1** inside the form and change **Width** to `400`

    ![A screenshot of the photo selected inside the canvas and a border around the size field changed to 400 in the properties pane](03-1/media/ex2-t4-image5.png)

9.  Expand the form and select the **Reserved by_DataCard1** data card.

    ![A screenshot of a border around reserved by data card selected under edit form 1](03-1/media/ex2-t4-image5_1.png)

10. Go to the **Properties** pane, select the **Advanced** tab and select **Unlock**.

    ![A Screenshot with an arrow pointing to the lock icon under the advanced tab](03-1/media/ex2-t4-image5_2.png)

11. Search for **display** and change the **DisplayMode** value to **DisplayMode.View** 

12. Select the **Browse gallery** under **LeftContainer** in the treeview.

13. Select **Items** on the formula bar and replace the value with formula below. This formula will filter the gadgets to show only the available gadgets.

    ```Filter(Gadgets, Availability <> [@Availability].'Picked up')```

    ![Filter data - screenshot](03-1/media/lab4-ex1-t1-35.png)

14. Select the **Image1** inside the gallery.

    ![A Screenshot with an arrow pointing to image 1 inside the gallery](03-1/media/ex2-t4-image7.png)

15. Go to the formula bar and verify that the value of the **Image** property is set to the formula: **ThisItem.Photo**.

    ![A Screenshot with an arrow pointing to image 1 inside the gallery](03-1/media/lab4-ex1-t1-36.png)

16. Select the **Data** tab (database icon) in the left navigation, select the **...More actions (1)** button of the **Gadgets** table and select **Refresh (2)**.

    ![A Screenshot with an arrow pointing to the ellipsis icon for more actions and a border around the refresh button](06/media/gadgets.png)

17. Select **Save** and wait for the app to be saved.

18. Select **Preview the app**.

19. Select **+ New record**.

    ![A screenshot of a border around the new record button](03-1/media/ex2-t4-image10.png)

20. Fill out the form and select **Tap or click to add a picture**.

    ![A Screenshot with an arrow pointing to the tap or click to add a picture button](03-1/media/ex2-t4-image11.png)

21. Provide your own photo or choose one from the Lab Resources folder.

22. Select **Save**.

    ![A Screenshot with an arrow pointing to the tick icon to save](03-1/media/ex2-t4-image12.png)

23. **Add** a few more new records.

24. Your app should now look like the image below. Select **X** to close the preview..

    ![A screenshot of the running app with an arrow pointing to the cross icon to close the preview](03-1/media/ex2-t4-image13.png)

25. **Do not** navigate away from this screen.


### Task 4: Update Dataverse rows

In this task, you will add buttons that will let users reserve and/or pick up item, you will also update the rows in Dataverse as reserved or picked up.

1.  Select **App** from the Tree view and set the **OnStart** property to the formula below. This formula will create a variable named CurrentUser and set its value to the first user that matches the logged in user's email.

    ```Set(CurrentUser, First(Filter(Users, 'Primary Email' = User().Email)))```

    ![A screenshot with a border around app selected in the screens tab on the left and another border around the formula bar with the relevant command entered in](03-1/media/lab4-ex1-t1-41.png)

2.  Select App, select **ellipsis** and select **Run OnStart**.

3.  Select the **RightContainer1**.

    ![A screenshot with a border around the RightContainer1 element selected](03-1/media/ex2-t5-image2.png)

3.  Select the **+** Insert button and select **Button**.

    ![A Screenshot with an arrow pointing to the plus icon to insert and a border around the button option](03-1/media/lab4-ex1-t1-42.png)

4.  Select the **Tree view**, double-click on the button you just added and rename it `Reserve Button`.

5.  Set the **Text** property of the Reserve Button to **Reserve**.

    ![A screenshot with the text "Reserve Button" highlighted as the new name for the button you added](03-1/media/lab4-ex1-t1-43.png)

6.  **Move** the Reserve Button and place it next to the Gadget Image.

    ![A screenshot of the Reserve button selected and moved next to the image on the right hand side](03-1/media/ex2-t5-image5.png)

7.  Set the **DisplayMode** property of the Reserve Button to the formula below. This formula will disable the button if the selected item is not available.

    ```If(BrowseGallery1.Selected.Availability = [@Availability].Available, DisplayMode.Edit, DisplayMode.Disabled)```

8.  Set the **OnSelect** property of the Reserve Button to the formula below. This formula will update the selected record by setting the reserved by value to the current user and the availability value to reserved.

    ```Patch(Gadgets, BrowseGallery1.Selected, {Availability: [@Availability].Reserved, 'Reserved by': CurrentUser})```

    ![A screenshot of the Reserve button selected and moved next to the image on the right hand side](03-1/media/lab4-ex1-t1-45.png)

9.  Set the **Visible** property of the Reserve Button to the formula below. This formula will hide the button if the user is creating a new record.

    ```If(EditForm1.Mode = FormMode.View, true, false)```

    ![A screenshot of the Reserve button selected and moved next to the image on the right hand side](03-1/media/lab4-ex1-t1-46.png)

10. Select the **RightContainer1** again.

11. Select the **+** Insert button and select **Button** again.

12. Select the **Tree view**, double-click on the button you just added and rename it to `Picked Up Button`.

12. Set the **Text** property of the Reserve Button to `Picked Up`.

13. Adjust the **width** property to **150** and **move** the Picked Up Button and place it to the right of the Reserve Button.

    ![A screenshot showing the Picked Up button selected and moved to the right of the Reserve button](03-1/media/ex2-t5-image7.png)

14. Set the **DisplayMode** value of the Picked Up Button to the formula below. This formula will disable the button if the selected item is reserved and the reserved by user is not the current user.

    ```If(BrowseGallery1.Selected.Availability = [@Availability].Reserved And BrowseGallery1.Selected.'Reserved by'.'Primary Email' <> CurrentUser.'Primary Email', DisplayMode.Disabled, DisplayMode.Edit)```

15. Set the **OnSelect** value of the Picked Up Button to the formula below. This formula will update the selected record by setting the reserved by value to the current user and the availability value to picked up. The second formula will select the first item of the gallery.

    ```Patch(Gadgets, BrowseGallery1.Selected, {Availability: [@Availability].'Picked up', 'Reserved by': CurrentUser});Select(BrowseGallery1,1)```

16. Set the **Visible** value of the Picked Up Button to the formula below. This formula will hide the button if the user is creating a new record.

    ```If(EditForm1.Mode = FormMode.View, true, false)```

17. Select **Save** to save your changes.

18. Do not navigate away from this page.


### Task 5: Add search

In this task, you will add search capability to your application.

1.  Select the **RightContainer1**.

2.  Select the **+ Insert** menu, select **Icons** and then select **+ Add**.

3.  Place the icon above the form.

    ![A screenshot of the plus icon selected](03-1/media/ex2-t6-image1.png)

4.  Select the icon from the tree view, go to the **Properties** and select **Search** for Icon.

    ![A screenshot with a border around the Search option selected as the icon](03-1/media/ex2-t6-image2.png)

5.  Select the **+** Insert menu and select **Text box**.

6.  Select the **Tree view**.

7.  Select the text box you just added and rename it `Search Box`

8.  **Move** the Search Box to the right of the icon.

    ![A screenshot of the Search Box placed to the right of the icon](03-1/media/ex2-t6-image4.png)

9.  Select the **Search Box** and set **OnChange** value to the formula below. This formula will reset the gallery.

    ```Reset(BrowseGallery1)```

10. Select the **BrowseGallery1** under **LeftContainer1** and change the **Items** formula to the formula below. The formula is incomplete, we will complete it in the next step.

    ```Filter(Search(Gadgets, 'Search Box'.Value, ), Availability <> [@Availability].'Picked up')```

11. Place your cursor after **'Search Box'.Value** and enter `name`. You should see a suggestion with crxxx_name, select the suggested column.

12. Add a comma after the name column you just selected and enter `description` and select the suggested column again.

13. Your formula should now look like the image below. This formula will search the name and description columns of the gadgets table for whatever the user enters in the text box and filter out the picked up items.

    ![Suggested description column - screenshot](03-1/media/ex2-t6-image7.png)

14. Select the **Search Box** from the RightContainer1.

15. Go to the formula bar and clear the **Value** text.

    ![A screenshot with a border around the formula bar](03-1/media/ex2-t6-image8.png)

16. Select **Save** to save your changes.


## Exercise 3: Test and publish application

In this exercise, you will test, publish and give colleagues permission to use the application.

### Task 1: Test application

In this task, you will test the application.

1.  Select the **Preview** button.

    ![A screenshot with an arrow pointing to the Preview button](03-1/media/ex3-t1-image1.png)

2.  The **Reserve** and **Picked Up** button should be visible and enabled.

3.  Search for `cable`. The gallery should show items that have the text **cable** in the name or description column.

5.  Select one of the items, the **Reserved by** column value should be empty.

6.  Select the **Reserve** button.

    ![A screenshot of a border around the Reserved by field and an arrow pointing to the Reserve button](03-1/media/ex3-t1-image3.png)

7.  The **Reserve** button should become disabled and the **Reserved by** value will be set to your username. Select the **Picked Up** button.

    ![A screenshot with a border around the reserved by field with your username and another border around the now-disabled reserve button](03-1/media/ex3-t1-image4.png)

8.  The item should no longer show up on the gallery and the first item of the gallery should get selected.

9.  **Close** preview mode.

10.  Do not navigate away from this page.


### Task 2: Publish application

In this task, you will publish the application to Teams.

1.  Select the **Publish to Teams** button.

    ![A Screenshot with an arrow pointing to the publish to teams button](03-1/media/ex3-t2-image1.png)

2.  Select **Next**.

3.  Select the **+** to add app as a tab.

    ![A Screenshot with an arrow pointing to the plus icon for add app as a tab in the general box](03-1/media/ex3-t2-image2.png)

4.  Select **Save and close**.

5.  Select **Teams** and select the new **Upcycle** tab.

    ![A Screenshot with an arrow pointing to the upcycle button](03-1/media/ex3-t2-image3.png)

6.  The app should load. If the app is not loaded, **refresh** the page.

    ![A screenshot of the loaded app](03-1/media/ex3-t2-image4.png)

7. **Test** the application in Teams and make sure it behaves as you expect.


### Task 3: Give permissions

In this task, you will give your colleagues permission to create new items, edit items they created, delete items they created and read items created by other people.

1.  Select **Power Apps** and select the **See more** link.

    ![A screenshot with a border around the power apps button on the left side of the window and an arrow pointing to the see more link in the recent apps](03-1/media/ex3-t3-image1.png)

2.  Open the **Gadget** table.

3.  Select **Manage permissions**.

    ![A Screenshot with an arrow pointing to the manage permissions button](03-1/media/ex3-t3-image2.png)

4.  Select **Member**, select the **Collaborate** permission and select **Save**.

    ![A screenshot of the collaborate permission selected](03-1/media/ex3-t3-image3.png)

5.  You may wish to test the application with another user in your tenant and see how it behaves.

### Review
In this lab, you have completed:
- Get started with Microsoft Dataverse for Teams.
- Created application.
- Tested and published application. 

### You have successfully completed the lab
