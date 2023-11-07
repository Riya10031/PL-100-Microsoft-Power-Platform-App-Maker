# Lab 07: Power BI


> Effective November 2020:
> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)
>


## Lab Scenario

In this lab, you will build a Power BI dashboard that visualizes data about problems reported by company employees.

## Lab Objectives

-  Exercise 1: Prepare environment & data
-  Exercise 2: Create Power BI Report
-  Exercise 3: Create Power BI Dashboard
-  Exercise 4: Embed Power BI report
-  Exercise 5: Power BI embedded canvas

## High-level lab steps

We will follow the below steps to design and create the Power BI dashboard:

-   Connect to tables in Microsoft Dataverse 
-   Transform the data to include user-friendly descriptions for the related Rows (lookups)
-   Create and publish a report with various visualizations of the information about problem reports
-   User natural language query to build additional visualizations
-   Build mobile view
-   Embed the Company 311 Power BI report to Microsoft Teams

## Prerequisites

* Must have completed **Lab 02.1: Data model and model-driven app**
* Permissions to install programs on your computer (required for Power BI Desktop installation)

## Things to consider before you begin

-   Who is the target audience of the report?
-   How will the audience consume the report? Typical device? Location?
-   Do you have sufficient data to visualize?
-   What are the possible characteristics you can use to analyze data about the visits?

## Detailed steps

### Exercise 1: Prepare environment & data  

**Objective:** In this exercise, you will install and configure Power BI Desktop and configure a connection to Microsoft Dataverse. 

> **IMPORTANT**
>
> If you do not have required permissions to install desktop applications or experience difficulties in configuring Power BI Desktop and connecting it to the data, follow **Addendum: Import sample data** and then continue on **Exercise 2** but using Power BI service instead of Power BI Desktop.

#### Task 1: Configure Power BI Desktop

1.  If you do not have Power BI Desktop installed, navigate to [https://aka.ms/pbidesktopstore](https://aka.ms/pbidesktopstore) to download and install Power BI app.

    > **IMPORTANT**
    >
    > If you experience issues installing Power BI Desktop using Microsoft Store, try the standalone installer that can be downloaded from [https://aka.ms/pbiSingleInstaller](https://aka.ms/pbiSingleInstaller).

2.  Open Power BI Desktop and select **Get started**.

3.  Subscribe to the email list or select **Maybe later** and select **Close**.

    **Note:** If you were signed into Power BI Desktop previously, select **File** > **Sign out**. 

4.  Enter your email address and select **Continue**. Sign in if prompted or select **File** > **Sign in** to sign in.

5.  Select **Work or school account** and select **Continue**.

6.  Sign in using your M365 credentials and select **No, sign into this app only**. 


#### Task 2: Prepare Data

1.  Open Power BI Desktop if it is not already open.

2.  Select **Get data** > **Dataverse**.

3.  Select **Sign in**.

    ![A screenshot of the dataverse selected in the power platform window](05/media/image-6-4.png)

4.  The connection details dialog will open up. If you are not signed in, select **Sign in** and follow the prompts to sign in. Select **Connect**. 

5.  Expand environment node. Using `lh_` to filter, select the **lh_building**, **lh_department**, **lh_problemreport** tables and select **Load**. Wait until the load is complete.

    ![A Screenshot with an arrow pointing to the load button](05/media/image-6-7.png)

6.  On the **Connection settings** window, choose **DirectQuery** and select **OK**.

7.  Select the **Model** icon on the left vertical toolbar.

    ![A Screenshot with an arrow pointing to the model icon on the left vertical toolbar](05/media/image-6-8.png)

8.  Power BI should detect the relationships between the tables. The relationship should look like the image below.

    ![A screenshot of the relationship between the table. There should be three main panels, Ih_building, Ih_problemreport, and Ih_department](05/media/image-6-9.png)

9. Select the **Report** icon on the left side of the canvas.

    ![A Screenshot with an arrow pointing to the report icon on the left toolbar](05/media/image-6-10.png)

10. Expand the **lh_problemreport** node in the **Data** panel. 

11. Select the **...** More options button of the **lh_ProblemReport** table. 

    ![A Screenshot with an arrow pointing to the ellipsis for more options](05/media/image-6-11.png)

12. Select **New column**. 

    ![A screenshot of a border around the new column button](05/media/image-6-12.png)

13. Complete the formula as below and press ENTER or select the checkmark button. That will add a new column with the building name into the problem report data.

    ```Building = RELATED(lh_Building[lh_name])```

    ![A Screenshot with an arrow pointing to the checkmark icon](05/media/image-6-13.png)

14. Repeat the three previous steps on **lh_problemreport** node to add a column **Department** with the below formula.

    ```Department = RELATED(lh_Department[lh_name])```

15. Select the **...** menu next to the **lh_problemreportid** column of the **lh_problemreport** table and select **Rename**. Enter **Problem Report** as the column name.

16. Select the **...** menu next to the **statuscodename** column and select **Rename**. Enter `Status` as the column name.

17. Save work in progress by selecting **File** > **Save** and enter `Problem management` as a filename.


### Exercise 2: Create Power BI Report 

**Objective:** In this exercise, you will create a Power BI report based on data from Microsoft Dataverse tables.

#### Task 1: Create Chart and Time Visualizations

1.  Click on **Report view**

    ![A Screenshot with an arrow pointing to the Report view](05/media/image-6-31.png)

2.  Select the **Pie chart** icon in the **Visualizations** panel to insert the chart.

    ![A Screenshot with an arrow pointing to the pie chart icon](05/media/image-6-14.png)

3.  Expand **lh_ProblemReport** table in the **Data** panel, drag **Building** Column and drop it into **Legend** target box.

4.  Drag **Problem Report** Column and drop it into **Values** target box.

    ![A Screenshot with an arrow pointing to the direction the problem report needs to be dragged from the fields column into the values field](05/media/image-6-15.png)

5.  Resize the pie chart using corner handles so that all chart components are visible. Your report should now look like this:

    ![A screenshot with a border around the legend next to pie chart after resizing to make all your components visible](05/media/image-6-16.png)

6.  Select the report's design surface outside of the chart area. Select **New visual** on the Power BI ribbon then select **stacked column** chart in **Visualizations** pane. 

    ![A Screenshot with an arrow pointing to the stacked column chart icon](05/media/image-6-17.png)

7.  Drag **Problem Report** Column and drop it into **Y-axis** target box.

8.  Drag **Status** Column and drop it into **X-axis** target box.

9.  **Resize** the chart as required using the corner handles.

10.  **Test** the report interactivity:

    * Select various building slices on the pie chart and observe changes on the stacked column chart.
    * Select various bars on the stacked column chart and observe changes on the pie report.

    ![A Screenshot with an arrow pointing to the pie chart to observe changed to the data after changing data on the stacked column chart](05/media/image-6-18.png)

11. Select the **Insert**, and select **Q&A**.

    ![A Screenshot with an arrow pointing to the Q&A button](05/media/image-6-addbutton.png)

12. Select **Turn on Q&A** and wait for the Q&A to get ready.

13. Enter **bar count of problem reports by building**. You should see a bar chart.

    ![A screenshot of the relevant text typed into the Q&A field](05/media/image-6-QAchart.png)

14. The dashboard now has Q&A enabled. Select the **...** More options button of the Q&A visual and select **Remove**.

    ![A Screenshot with an arrow pointing to the ellipsis icon for more options and a border around the remove button](05/media/image-6-removevisual.png)

15. Save work in progress by selecting **File | Save**.


### Exercise 3: Create Power BI Dashboard

#### Task 1: Publish Power BI Report

1.  Navigate to [Power BI Service](https://app.powerbi.com)

2.  Select **Workspaces** and select **Create a workspace**.

    ![A Screenshot with a box around the workspaces button and an arrow pointing to the create a workspace button](05/media/image-6-createworkspace.png)

3.  Enter **311 Workspace** for Workspace name and select **Save**.

4.  Go back to the Power BI desktop application, select the **Home** tab, and select **Publish**.

    ![A Screenshot with an arrow pointing to the publish button](05/media/image-6-19.png)

5.  Select **311 Workspace** as the destination.

6.  **Wait** until publishing is complete and open the **<name of your report\>.pbix** file in Power BI.

    ![A Screenshot with an arrow pointing to the button to open your report](05/media/image-6-20.png)

    This will open the published report in the browser.

> **NOTE**
>
> If you are getting an error on PowerBI Service with message "the data source is missing credentials and cannot be accessed", follow the below steps:
>
> 1. Select **311 Workspace** and select the **Problem Management** dataset.
> 2. Expand Refresh dropdown and select **Schedule refresh**.
> 3. Expand **Data Source credentials** section and select **Edit Credentials**.
> 4. Select **OAuth2** for **Authentication** Method and **Organizational** for **Privacy level setting**.
> 5. Select **Sign in**. This will resolve the issue for report and it should display properly on Power BI.


#### Task 2: Create Power BI Dashboard

1.  Click on **311 Workspace**. If you don't see it in your menu, select **Workspaces** and then **311 Workspace**

2.  Select the **Problem management** with a type **Report**. 

    ![A screenshot with a border around the problem management option under reports](05/media/image-6-21.png)

3.  Select **Pin to a dashboard** on the menu. Depending on the layout you may need to press **...** to show additional menu items.

    ![A Screenshot with an arrow pointing to the ellipsis icon for more options and a border around the pin to dashboard option](05/media/image-6-22.png)

4.  Select **New dashboard** on **Pin to dashboard** prompt.

5.  Enter **Problem Management Dashboard** as a **Dashboard name**, select **Pin live**.

    ![A screenshot of the pin to dashboard prompt and the dashboard name changed](05/media/image-6-23.png)

6.  Select **311 Workspace** node, select **Problem Management Dashboard**.

7.  Test interactivity of the pie and bar charts that are displayed.


#### Task 3: Add Visualizations Using Natural Language

1.  Select **Ask a question about your data** on top of the dashboard.

    ![A Screenshot with an arrow pointing to the ask a question about your data button at the top of your dashboard](05/media/image-6-24.png)

2.  Enter **funnel count of problem reports by status** in Q&A area. The funnel chart will be displayed.

3.  Select **Pin visual**.

    ![A Screenshot with an arrow pointing to the pin visual button](05/media/image-6-25.png)

4.  Select **Existing dashboard**, select **Problem Management dashboard**, select **Pin**.


#### Task 4: Build Mobile Phone View

1.  Select the **Problem Management dashboard** from **Dashboards** area.

2.  Select **Edit** and then select **Mobile Layout** from the drop-down box.

3.  **Rearrange** the tiles as desired.

    ![A photo of the mobile phone layout with tiles rearrange to display data](05/media/image-6-26.png)

4.  Select your report under **311 Workspace**. Make sure you select **Problem management with type **Report**.

5.  Select **File** and then select **Generate QR Code** from the drop down box.

    ![A Screenshot with an arrow pointing to the file button and a border around the generate a QR code button](05/media/image-6-27.png)

6.  If you have a mobile device, scan the code using a QR scanner app available on both iOS and Android platforms.

    > **NOTE**
    >
    > To access the dashboard and report you will have to sign in on the phone as the same user.

7.  Navigate and explore reports and dashboards on a mobile device. 


### Exercise 4: Embed Power BI report

In this exercise, you will add the Company 311 Power BI report to Microsoft Teams and to the Company 311 Admin Model-driven application as a way for management and staff to be able to view the reports from directly within Teams and the Model-driven application. 

#### Task 1: Setup Company 311 Team

In this task you will setup a Microsoft Teams team for the Lamna Healthcare Company, if you have not done so previously.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com) and sign in with the credentials you have been using previously.

2.  Select **Use the web app instead** on the welcome screen.

    ![A screenshot of the Microsoft Teams landing page and a border around the use the web app instead button](05/media/image-6-teams.png)

3.  When the Microsoft Teams window opens, dismiss the welcome messages.

4.  On the bottom left corner, choose **Join or create a team**.

5.  Select **Create a team**.

    ![A screenshot with a border around the join or create team button at the bottom of the window and another border around the create a team button](05/media/image-6-createteam.png)

6.  Press **From scratch**.

7.  Select **Public**.

8.  For the Team name choose **Company 311** and select **Create**.

9.  Select **Skip** adding members to Company 311.


#### Task 2: Embed Power BI report to Teams

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com).

2.  Select the **General** channel of the **Company 311** team.

3.  On the top of the page, press the **+** symbol to add a new tab.

    ![A screenshot of the general channel of the company 311 team](05/media/image-6-addpowerbitab.png)

4.  Search for **power** and select **Power BI** from the results.

5.  Expand the **311 Workspace** and select the report you created earlier in this lab, then select **Save**.

    ![A screenshot of a prompt to which appears once you select Power BI](05/media/image-6-choosepowerbireport.png)

6.  You should now see your Power BI report in a tab in Microsoft Teams.

    ![A screenshot of your Power BI report in a tab in Microsoft Teams](05/media/image-6-powerbi.png)


#### Task 3: Embed Power BI report to Model-driven app

1.  Navigate to [Power BI](https://app.powerbi.com/home).

2.  Select **Data hub**.

    ![A screenshot of a border around the datasets button](05/media/image-6-datasets.png)

3.  Hover over the dataset you created, select the **...** More options button, and select **Settings**.

    ![A Screenshot with an arrow pointing to the ellipses button for more options and a border around the settings button](05/media/image-6-datasetsettings.png)

4.  Select **Edit credentials**, located in the **Data source credentials** section.

5.  Select **OAuth2** for Authentication method, select **Organizational** for Privacy level setting, and select **Sign in**.

    ![A screenshot of the edit credentials window with all relevant text in each field](05/media/image-6-datasetconfiguration.png)

6.  Provide your credentials.

7.  Navigate to [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in your practice environment.

8.  Select **Solutions** and open the **Company 311** solution.

9.  Select **+ New** and select **Dashboard | Power BI embedded**.

    ![A Screenshot with an arrow pointing to the new button, dashboard selected, and a border around the Power Bi embedded option](05/media/image-6-newpowerbiembeddeddash.png)

10. Enter **Problem management** for **Display name**, select **Power BI report** for type, uncheck **Show reports in this environment only** and select **311 Workspace** for **Power BI workspace**, select **Problem management** for **Power BI report** and select **Save**.

    ![A screenshot of the New Power BI embedded data window with all relevant text in each field](05/media/image-6-powerbidashprop.png)

11.  Select **Publish all customizations** and wait for the publishing to complete.

12.  While still in the Company 311 solution, open the **Company 311 Admin** Model-driven application.

    ![A Screenshot with an arrow pointing to the company 311 admin option with another border around model-driven application in the type column in line with the correct company 311 admin option](05/media/image-6-editmodeldrivenapp.png)

13. In app designer make sure you have **Manage Problems** area selected. If not, click on the arrows and select **Manage Problems**.

    ![A screenshot of the app designer navigation area selector](05/media/image-6-editsitemap.png)

14. Select the ellipses next to **Navigation** title and select **New group**.

    ![A screenshot with a arrow pointing to the Group option under Add button](05/media/image-6-eddgroup.png)

15. Go to the **Properties** pane and enter **Reports** for **Title**.

16. Select the **Reports** group you just created, select **+ New**.

    ![A screenshot with a cursor pointing to the New button](05/media/image-6-eddsubarea.png)

17. Select **Dashboard** for Type and click **Next**. 

18. **Under Power BI dashboards** check the checkmark next to **Problem management** and then select **Add**.

    ![A screenshot of the subarea properties dialog with the relevant option selected in each field](05/media/image-6-subareaprop.png)

19. Select the **...** ellipsis icon next to the **Reports** group and select **Move up**. 

20. Select **Save**, then select **Publish**, wait for the publishing to complete and then select **Play**. 

    ![A screenshot of the top-level menu with Save, Publish, and Play buttons. Cursor is pointing to the Save button](05/media/image-6-savepublishplay.png)

21. The report should load.

    ![A screenshot of your problem management report](05/media/image-6-PowerBIinModel.png)

22. Interact with report and make sure it behaves as expected.


### Exercise 5: Power BI embedded canvas

In this exercise, you will add embedded canvas application to Power BI as a visual.

#### Task 1: Add canvas

1.  Navigate to [Power BI](https://app.powerbi.com).

2.  Select **Workspaces** and then select to open **311 Workspace**.

3.  Open the **Problem management** report.

4.  Select **Edit**.

5.  **Resize** and **reposition** the visuals as shown below.

    ![Power BI visuals - screenshot](05/media/image-6-PowerBIVisuals.png)

6.  Select an empty area of the canvas, go to the **Visualizations** pane and select **Power Apps for Power BI**.

    ![Power Apps for Power BI - screenshot](05/media/image-6-powerappsforpowerbi.png)

7.  Select the Power BI visual you just created, expand the **lh_problemreport** table select **Problem Report** column. Drag the **Problem Report** column into the **Add data fields here** can be tracked under the **Visualizations >> PowerApps Data**

    ![Table column - screenshot](05/media/image-6-tablecolumn.png)

8.  Select your practice environment and select **Create new**.

    ![create app - screenshot](05/media/image-6-createembeddedapp.png)

9.  A **new browser tab** should open and load the **Power Apps Studio**.

10. Do not navigate away from this page.


#### Task 2: Customize the app

1.  Right-click on the **Gallery** and select **Delete**.

    ![Delete gallery button - screenshot](05/media/ex_5_deletegallery.png)

2.  Select **Settings** from the toolbar. 

3.  Select the **Display** tab.

4.  Change the **Orientation** to **Landscape** and select **Apply** on the popup. 

5.  Close the **Settings** window. 

6.  Select **Data** and select **Add data**.

    ![Add data - screenshot](05/media/ex_5_adddata.png)

7.  Select the **Problem reports** table.

    ![Select data table - screenshot](05/media/ex_5_datatable.png)

8.  From the **Tree view**, select the **App** object.

9.  Select the **OnStart** property of the **App** object (found in the **Advanced** tab) and set it to the formula below. This formula will create two variables one to keep track of the current index of the reports table and another to keep track of the current item row.

    ```Set(currentIndex,1);Set(CurrentItem, LookUp('Problem Reports', 'Problem Report' = GUID(Last(FirstN([@PowerBIIntegration].Data,currentIndex)).'Problem Report'))) ```

    ![A screentshot showing OnStart property set to the expression described on the previous step](05/media/ex_5_apponstart.png)

10. Select the **+ Insert** button, expand **Media** group, then select **Image**.

11. Set the **Image** value to the formula below.

    ```CurrentItem.Photo```

12. Select the **...** menu button of the **App** object and select **Run OnStart**.

    ![Run app OnStart - screenshot](05/media/ex_5_runonstart.png)

13. The photo from the Problem Report should load. If you are not seeing the photo, then go to the Admin **Model-driven App** and add photo to any Problem Report records where the **Photo** field is **empty**. 

    ![Current image with photo - screenshot](05/media/ex_7_imagephoto.png)

14. Set the **X** value of the image to **0**.

15. Set the **Y** value of the image to **0**.

16. Set the **Width** value of the image to the formula below.

    ```Parent.Width```

17. Set the **Height** value of the image to the formula below.

    ```Parent.Height```

18. The image should fill the screen.

    ![Image position - screenshot](05/media/ex_7_imageposition.png)

19. Do not navigate away from this page.


#### Task 3: Add controls

1.  Select the **Insert** tab and select **Text label**.

2.  Select **Label1** from the tree view and set the **Text** value to the formula below.

    ```CurrentItem.Title```

3.  Set the **Height** value of the label to **60**.

4.  Set the **X** value of the label to **0**.

5.  Set the **Y** value of the label to formula below.

    ```Parent.Height - Self.Height```

6.  Set the the **Width** value of the label to formula below.

    ```Parent.Width```

7.  Set the **Fill** value of the label to **RGBA(0, 108, 191, .5)**.

8.  Set the **Color** value of the label to **RGBA(255, 255, 255, 1)**.

9.  Set the **Align** value to the formula below.

    ```Align.Center```

10. The label should now look like the image below. If you don't see the title, select the **...** button of the **App** object and select **Run OnStart** again.

    ![Resized label - screenshot](05/media/ex_7_resizedlabel.png)

11. Select **+ Insert**, enter **next** in the search box, then select **Next arrow** under **Icons**.

12. Double-click on the name of the icon you just added and rename it **Next icon**.

13. Select **+ Insert**, enter **back** in the search box, then select **Back arrow** under **Icons**.

14. Double-click on the name of second icon you just added and rename it **Back icon**.

15. Drag and place the the **Next icon** above the right side of the label.

16. Drag and place the the **Back icon** above the left side of the label.

17. The icons should now look like the image below.

    ![Icon location - screenshot](05/media/ex_7_iconlocation.png)

18.  Select the **Next icon** and set the **OnSelect** value to the formula below.

    ```UpdateContext({CurrentItem: LookUp('Problem Reports', 'Problem Report' = GUID(Last(FirstN([@PowerBIIntegration].Data,currentIndex+1)).'Problem Report'))});UpdateContext({currentIndex: currentIndex+1})```

19.  Set the **DisplayMode** value of the **Next icon** to the formula below.

    ```If(currentIndex = CountRows([@PowerBIIntegration].Data), DisplayMode.Disabled, DisplayMode.Edit)```

20. Select the **Back icon** and set the **OnSelect** value to the formula below.

    ```UpdateContext({CurrentItem: LookUp('Problem Reports', 'Problem Report' = GUID(Last(FirstN([@PowerBIIntegration].Data,currentIndex-1)).'Problem Report'))});UpdateContext({currentIndex: currentIndex-1})```

21. Set the **DisplayMode** value of the **Back icon** to the formula below.

    ```If(currentIndex > 1, DisplayMode.Edit, DisplayMode.Disabled)```

22. Select **+ Insert**, enter **check** in the search box, then select **Check** under **Icons**.

23. In the tree view, double-click **Icon1** and rename the Check icon to **Complete icon**. 

24. Move the **Complete icon** to the top right of the screen.

25. Set the OnSelect of the **Check icon** to the formula below. This formula will update the status of the row to completed and then refresh Power BI.

    ```Patch('Problem Reports', CurrentItem, {'Status Reason': 'Status Reason (Problem Reports)'.Completed}); PowerBIIntegration.Refresh()```

26. Select **Play**.

27. Select the **next** and **back** icons and make sure the image changes.

28. **Close** the preview.

29. Select the **Save** button.

30. Enter **Power BI embed app** for **Name**.

31. Select **Save**.

32. Select the **Publish** button. Select **Publish this version**.

33. **Close** the app studio browser window or tab.

34. You should now be back on the Power BI report. Select **Refresh** on the top header. 

35. Select the **Next** and **Back** icons to make sure the application loads the images.

    ![Canvas inside Power BI report - screenshot](05/media/ex_7_canvasembedded.png)

36. Select the **Completed** column of the stacked column chart and make a note how many rows are completed.

37. Select any column of the stacked column chart apart from **Completed**. Select the **next** icon to see the next image.

38. Select the **Complete** icon.

    ![Complete status of problem - screenshot](05/media/ex_7_complete.png)

39. The completed count should increase. If the completed count doesn't increase, select refresh and wait for the visuals to be refreshed.

    ![Increased completed count - screenshot](05/media/ex_7_increasedcount.png)

40. **Save** the report.


## Challenges

* Dashboards and reports to include drilldown to individual reports with photos.

* Report and analyze problem patterns and trends.

* Problem resolution status visualization as a funnel.


## Addendum

### Import sample data

In this exercise you will import sample data into Power BI service. That allows you to complete the lab exercises even if do not have required permissions to install desktop applications, or experience difficulties in configuring Power BI Desktop and connecting it to the data. After completion of this exercise you can skip **Exercise1** and start the lab on **Exercise 2** using Power BI service ([https://app.powerbi.com](https://app.powerbi.com)) instead of Power BI Desktop. 

1.  Download [problem-reports-data.pbix](05\Resources\problem-reports-data.pbix) and save on your computer.

2.  Navigate to [Power BI](https://app.powerbi.com/).

3.  Select **311 Workspace**.

4.  Expand **+New** and select **Upload a file**.

    ![A Screenshot with an arrow pointing to the new button and another arrow pointing to the upload a file button](05/media/image-6-29.png)

5.  Select **Local File**.

6.  Locate and select **problem-report-data.pbix** file that you've downloaded earlier.

7.  Once data load is complete, select **problem-reports-data** report.

8.  Select **...** then select **Edit**.

    ![A Screenshot with an arrow pointing to the ellipses icon for more options and the edit button selected](05/media/image-6-30.png)

9. You can now start **Exercise 2: Create Power BI Report** of this lab.

    > **NOTE**
    >
    > The sample data contained in **pbix** file may differ from the data present in the Dataverse instance. If reports are built using imported file, some of the visual elements and functionality may vary as a result.
