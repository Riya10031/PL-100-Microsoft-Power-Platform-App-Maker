# Course Introduction
 
> -  Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)
 
# Lab 02.1: Data model and model-driven app

## Lab Scenario

In this lab you will be implementing the data model for the solution and building a model-driven app that will be used for tracking problems and managing the overall effort.

## Lab Objectives
 
Though this lab, you will be able to complete and gain insights into the following exercises:

- Exercise 1 : Create publisher and solution  
- Exercise 2 : Implement the data model 
- Exercise 3 : Configure forms and views 
- Exercise 4 : Compose a basic model-driven app 
- Exercise 5 : Input data and refine some views, import some problem reports 

### Exercise 1: Create publisher and solution

In this exercise, you will create a custom solution publisher and a solution. This solution will be used in all the labs for this course to keep all the components together. 

#### Task 1: Create publisher and solution

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the practice environment you created. 

1.  From the left navigation pane, select **Solution**.

1. Select **Create a database** and on the **New database** page, select **Create my database**.

1. Select **+ New solution**. 

1. For **Display name**, enter `Company 311` 

1.  Select **+ New publisher**, under the **Publisher** field. 

    ![A Screenshot with an arrow pointing to the new publisher button](02-1/media/image1(1).png)

1.  Enter the following credentials, and select **Save**.

    |**Settings**|**Value**|
    |------------|---------|
    |Display name|**Lamna Healthcare**|
    |Name|**lamnahealthcare**|
    |Prefix|**lh**|
    |Choice value prefix|**88186**|

    ![A screenshot of the new publisher properties pane](02-1/media/image105(1).png)

1.  Select **Lamna Healthcare (lamnahealthcare) (1)** from the **Publisher** dropdown menu. 

1.  Select **Create (2)**. 

    ![A screenshot of the new solution pane](02-1/media/image3(1).png)


### Exercise 2: Implement data model

In this exercise, you will create Tables, Columns, and the Relationships you identified when you designed the data model for the Company 311 app.

#### Task 1: Create Tables

1.  In the [Power Apps maker portal](https://make.powerapps.com/) page, make sure you are in the correct environment. Select **Solutions** and open the **Company 311** solution you created in Exercise 1.

2.  Select **+ New** \> **Table** \> **Table**. 

3.  Enter `Building` for **Display name** and select **Save**.

    ![A screenshot of the new table window with the relevant value in each field](02-1/media/image5(1).png)

4.  Select **All** from the tree view, in the **Objects** pane to display all solution objects and subcomponents. 

5.  Select **+ New** \> **Table** \> **Table** again.

6.  Enter `Department` for **Display name** and select **Save**.

    ![A screenshot of the new table window with the relevant value in each field](02-1/media/image7(1).png)

7.  Select **All** from the tree view, in the **Objects** pane to display all solution objects and subcomponents. 

8.  Select **+ New** \> **Table** \> **Table** one more time.

9.  Enter `Problem Report` for **Display name**.

    ![A screenshot of the new table window with the relevant value in each field](02-1/media/image8(1).png)

7.  Select the **Primary column** tab, enter `Title` for **Display name**.

    ![A screenshot of the new table window with the Primary column tab selected and the word Title entered in the Display name textbox](02-1/media/image8-1(1).png)

10. Select the **Properties** tab, expand **Advanced options**, then scroll to the **Rows in this table** section. 

11. Check the **Can be added to a queue** checkbox and select **Save**. 

    ![A screenshot of the Rows in this table section with Can be added to a queue checkbox selected](02-1/media/image10(1).png)

    >**Note:** Enabling queues for Problem Report table allows rows to be associated with one or more queues to help facilitate routing problem reports to the different departments. Once this option is enabled, it can't be turned off. 

12. Select **All** from the tree view in the **Objects** pane. The tables you created should now be visible in the list view and in the tree navigation. 

    ![Screenshot of the Company 311 solution page with all components visible. The component list contains three tables Building, Department, Problem Report](02-1/media/image10-1(1).png)


#### Task 2: Add Columns

In this task, you will add Columns to the Problem Report Table.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution you created in exercise 1.

3.  Select the **Problem Report** Table.

4.  There are many ways to add a new column to the table. For this lab, select **+ New (1)**, then select **Column (2)** from the Schema group. 

    ![A screenshot of the solution page with +New menu expanded and cursor pointing to the Column item](02-1/media/image13(1).png)

5.  Enter `Location` for **Display name (1)**. Select **Text > Single line of text > Plain text** for **Data type (2)**. 

    ![A screenshot of a New column form with Data type dropdown expanded with Text > Plain text option selected](02-1/media/image14-1(1).png)

6. Expand the **Advanced options** section, change **Maximum character count** to `150`, then select **Save**. 

    ![A screenshot of expanded Advanced options section with the cursor pointing to Save button](02-1/media/image14(1).png)

7.  Select **+ New \> Column** from the top menu. 

8.  Enter the following credentials, and select **Save**.

    |**Settings**|**Value**|
    |------------|---------|
    |Display name|**Details**|
    |Data type|**Text \> Multiple lines of text \> Plain Text**|
    |Required|**Business required**|

    ![A screenshot of the details window with the relevant values in each field](02-1/media/image16(1).png)

9.  Select **+ New \> Column** again.

10.  Enter `Photo` for **Display name**, select **File > Image** for **Data type**, and select **Save**.

11.  Select **+ New \> Column**.

12.  Enter `Resolution` for **Display name**, select **Text \> Multiple lines of text \> Plain Text** for **Data type**, and select **Save**.

13.  Select **+ New \> Column**.

14.  Enter `Resolved On` for **Display name**, select **Date and time** for **Data type**, and select **Save**. 

15.  Select **All** from the tree view in the **Objects** pane. 

16.  Select **Publish all customizations** from the command bar and wait for the publishing to complete.

> **IMPORTANT**
>
> Do not navigate away from this page until all customizations have been published successfully.

#### Task 3: Edit Status Reason Choice

In this task, you will edit the Status Reason column of the Problem Report table.

1.  Make sure you are in the **Company 311** solution.

2.  In the **Objects** navigation tree expand **Tables**, expand **Problem Report**, select **Columns**. Locate and select the **Status Reason** column.

3.  Change the existing label for the **Active** option to `New`

4.  Select **+ New choice** and enter `Assigned` for **Label**.

5.  Select **+ New choice** and enter `In Progress` for **Label**.

6.  Select **+ New choice** and enter `Completed` for **Label**.

7.  Select **+ New choice** and enter `Won’t Fix` for **Label**.

8.  You should now have 5 options. Verify the **Default choice** is set as **New (1)** and select **Save (2)**.

    ![A screenshot of the Status Reason column properties with 5 options and New as Default choice](02-1/media/image25(1).png)

9.  Select **All** from the tree view in the **Objects** pane. 

10. Select **Publish all customizations** and wait for the publishing to complete.


#### Task 4: Relationships

In this task, you will create many-to-one relationships between the Problem Report table and the Building and Department tables.

1.  In the **Objects** navigation tree expand **Tables**, select and expand **Problem Report** table.

2.  Select **+ New \> Relationship \> Many-to-one**.

3.  Select **Building** for the **Related (One) (1)** table and select **Done (2)**.

    ![A screenshot of the many-to-one relationship settings](02-1/media/image29(1).png)

4.  Select **+ New > Relationship > Many-to-one** menu again.

5.  Select **Department** for **Related (One)** table and select **Done**.

6.  Select **All** from the tree view in the **Objects** pane. 

7.  Select **Publish all customizations** and wait for the publishing to complete. 


### Exercise 3: Configure form and views

In this exercise, you will configure form and views for the Problem Report table.

#### Task 1: Configure form

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and select the **Company 311** solution.

3.  In the **Objects** navigation tree expand **Tables**, expand **Problem Report** table.

4.  Select the **Forms** tab and open the **Information** form of type **Main**.

5.  Use the Zoom control at the bottom of the form to make the form large enough for you to work easily. Select the **General** tab. 

    ![A screenshot of the form designer with General form section selected.](02-1/media/image31(1).png)

6.  Go to the **Properties (1)** pane, change the **Label (2)** to `Problem details` and enter `section\_problem\_report` for **Name (3)**.

    ![A screenshot of the properties pane with the relevant text in each field](02-1/media/image32(1).png)

7.  While you still have the section selected, go to the **Table columns (1)** pane, and select the **Building (2)** Column. The Building Column will be added to the form.

    ![A screenshot of the form designer with Building column selected in the Table columns section.](02-1/media/image33(1).png)

8.  Add the **Details**, and **Photo** Columns to the form. Select the **Details** Column.

9. Go to the **Properties** pane and expand the **Formatting** section.

10. Change the **Form field height** to **4 rows**.

    ![A screenshot of the form field height set to 4 rows](02-1/media/image36(1).png)

11. Select the **Component (1)** from the top menu then select **1-column section (2)**.

    ![A screenshot of the form field height set to 4 rows](03-2/media/1-column.png)

12. A new section should be added to the form. Select the **New Section**.

13. Go to the **Properties (1)** pane, change the **Label (2)** to `Resolution details` and enter `section\_resolution\_details` for **Name (3)**.

    ![A screenshot of the section properties pane with the relevant text in each field](02-1/media/image40(1).png)

14. Select **Table columns** from the toolbar.

15. Add **Department**, **Status Reason**, **Resolved On**, and **Resolution** columns to the **Resolution details** section.

16. Select the **Resolution** Column.

17. Go to the **Properties** pane and, if necessary expand the **Formatting** section.

18. Change the **Form field height** to **4 rows**.

19. Your form should now look like the image below. Select **Save and publish**.

    ![A screenshot of the form field height set to 4 rows](03-2/media/newproblem.png)

20. Wait for the publishing to complete.

21. Select the **🡠 Back** button to return to the **Solution Explorer**.

    ![A screenshot of the form designer with the cursor over Back button inm the menu.](02-1/media/image43(1).png)


#### Task 2: Edit view

1.  In the **Problem Report** table, under **Data experiences**, select **Views**.

    ![A screenshot of the form field height set to 4 rows](03-2/media/problemreport.png)

2.  Open the **Active Problem Reports** view.

    ![A screenshot of the view list for Problem Report table with Active Problem Reports entry highlighted.](02-1/media/image44(1).png)

3.  Select **Building** in the **Table columns** list to add the **Building** column to the view.

4.  Select **Location**, **Status Reason**, and **Owner** columns to add them to the view.

5.  Go to the view **Properties** pane and select **Edit filters**.

    ![A Screenshot with an arrow pointing to the edit filters button](02-1/media/image47(1).png)

6.  Change the existing filter and set it to **Status Reason Equals New**.

    ![A Screenshot with an arrow pointing to the edit filters button](03-2/media/editfilter.png)

7.  Expand the values drop-down with Status Reason values where **New** is selected.

8.  Select **Assigned**.

9.  Select the drop-down again and select **In Progress**.

10. The filter should now look like the image below. Select **Ok**.

    ![A screenshot of the edit filters window with the condition Status Reason equals New, Assigned, and In Progress](02-1/media/image50(1).png)

11. Select **Save and publish**.


#### Task 3: Create view from existing

In this task, you will create a new view from the Active Problem Reports view.

1.  Select **Edit filters**.

    ![A screenshot with an arrow pointing to the Edit filters button](02-1/media/image51(1).png)

2.  Remove **In Progress** from the filter.

    ![A screenshot with an arrow pointing to the In Progress value in the condition for the Status Reason column.](02-1/media/image52(1).png)

3.  Remove **Assigned**, then remove **New** value form the filter.

4.  Select the drop-down list, then select **Completed**.

    ![A screenshot with an arrow pointing to the completed button from the drop down in the 3rd column](02-1/media/image53(1).png)

5.  Add **Won’t Fix** and **Inactive** values to filter.

6.  The filter should now look like the image below. Select **Ok**.

    ![A screenshot of the edit filters window with the following Status Reason values: Completed, Won't Fix, Inactive](02-1/media/image54(1).png)

7.  Select **Save As** button.

8.  Enter `Resolved Problems` for **Name (1)** and select **Save (2)**.

    ![A screenshot of the Save As window](02-1/media/image56(1).png)

9.  Select the **🡠 Back** button to return to the solution explorer.

    ![A Screenshot with an arrow pointing to the back button](02-1/media/image57(1).png)

10. Select **All** in the **Objects** navigation tree.

11. Select **Publish all customizations** and wait for the publishing to complete.


### Exercise 4: Compose model-driven application

In this exercise, you will create a model-driven application.

#### Task 1: Create new model-driven application

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New (1)> App (2)> Model-driven app (3)** from the command bar.

    ![A screenshot of the menu to create a new model-driven app](02-1/media/image60(1).png)

4.  Enter `Company 311 Admin` (1) for name and select **Create (2)**. 

    ![A screenshot of the New model-driven app window](02-1/media/image61(1).png)

5.  Select **Navigation** from the left menu. 

6.  In the properties pane, check **Enable Areas**.

    ![A screenshot of the navigation pane with navigation bar selected](02-1/media/lab02-ex4-t1-s5-b.png)

7.  Select **Area1**.

8.  Go to the **Properties** pane, enter `Manage Problems` for **Title (1)**, and enter `area_manage_problems` for **ID (2)**.

     ![A screenshot of the properties pane with the title and ID changed](02-1/media/lab02-ex4-t1-s8.png)

9.  Select **+ Add page** on the **Pages** menu.

     ![A screenshot of the properties pane with the title and ID changed](02-1/media/lab02-ex4-t1-s9.png)
   
10. Select **Next**.

11. Search for and select **Problem Report**.

12. Select **Add**.

    ![A screenshot of the adding Problem Reports](02-1/media/image65(1).png)
    
13. Select **New Group** in the navigation pane.

14. Go to the **Properties**, enter `Problems` for **Title (1)**, and enter `group_problems` for **ID (2)**.

    ![A screenshot of the adding new area](02-1/media/lab02-ex4-t1-s14.png)

16. Click on area selection and then select **New area**
    
    ![A screenshot of the adding new area](02-1/media/image107(1).png)

17. Go to the **Properties** pane, enter `Settings` for **Title (1)**, and enter `area_settings` for **ID (2)**.

    ![A screenshot of the properties pane with the title and ID changed](02-1/media/lab02-ex4-t1-s16.png)
    
18. Select **+ New** on the **Pages** menu.

19. Select **Next**.

20. Search for and select **Building**.

21. Search for and select **Department**.

22. Select **Add**

23. Select **New Group**.

24. Go to the **Properties** pane, enter **Taxonomy** for **Title**, and enter **group\_taxonomy** for **ID**.

25. The navigation should now look like the image below. Select **Save**.

    ![A screenshot of the navigation in Settings area](02-1/media/image108(1).png)

26. Select **Publish** to publish the sitemap and wait for the publishing to complete.

27. Select the **🡠 Back** button to return to the **Solution Explorer**.

28. Select **All** in the **Objects** navigation tree.

29. Select **Publish all customizations** and wait for the publishing to complete.

    ![A screenshot with an arrow pointing to the publish all customizations button](02-1/media/lab02-ex4-t1-s28.png)


### Exercise 5: Input data

In this exercise, you will input data to the Dataverse tables.

#### Task 1: Input data

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps (1)** and open the **Company 311 Admin (2)** application created in the previous exercise.

    ![A Screenshot with an arrow pointing to the Company 311 Admin app](02-1/media/lab02-ex5-t1-s2.png)

3.  Select **Change area**.

    ![A screenshot with an arrow pointing to chevron icon next to Manage Problems](02-1/media/lab02-ex5-t1-s3.png)

4.  Select the **Settings** area.

5.  Select **Departments** and select **+ New**.

6.  Enter `Information Technology` for **Name** and select **Save**.

    ![A screenshot showing the change in name to information technology](02-1/media/lab02-ex5-t1-s6.png)

7.  Select **Buildings**.

    ![A Screenshot with an arrow pointing to the buildings button under taxonomy](02-1/media/lab02-ex5-t1-s7.png)

8.  Select **+ New**.

9.  Enter `San Francisco Main Campus` for **Name** and select **Save & Close**.

10. Select **+ New** again.

11. Enter `London Paddington` for **Name** and select **Save & Close**.

    >**Note:** You should now have two Building rows.

12. Select **Change area**.

    ![A Screenshot with an arrow pointing to the chevron icon next to settings in the bottom left corner of the window](02-1/media/lab02-ex5-t1-s12.png)

13. Select **Manage Problems**.

14. Select **+ New**.

    ![A screenshot of the active problem reports page](02-1/media/image86(1).png)

15. Enter **Broken door** for **Title**, select **San Francisco Main Campus** for **Building**, enter **The main entrance door will not open all the way** for **Details**, and select **Save**.

    >**Note:** You cannot save images before creating the row in the database. Select **Save** and then you may upload a picture.

    ![A screenshot of the new problem report window with all relevant text in each field](02-1/media/lab02-ex5-t1-s15.png)

16. Select **Choose file** on the **Photo** field.

17. Select an image from your device. The sample image displayed below can be found [here](02-1/media/image89(1).png).

18. The image should now show on the form.

    ![A screenshot of a vector image of a door which should appear](02-1/media/image89(1).png)

19. Select **Save & Close**.


### Exercise 6: Import data

In this exercise, you will import sample data into the environment. Rows are imported by a Power Automate cloud flow that you will first import using a solution.

#### Task 1: Import solution

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Solutions** and select  **Import Solution**.

3.  Select **Browse**.

4.  Select the **DataImport.zip** solution file located in the **C:\PL100\PL-100-Microsoft-Power-Platform-App-Maker-prod\Instructions\Labs\02-1\Resources** and select **Open**.

5.  Select **Next**.

6.  Select **Next** again.

7.  Expand the **Select a connection** dropdown and select **+ New connection**.

8.  A new tab will open with a prompt to create the **Microsoft Dataverse** connection. 

9.  Select **Create**, authenticate if required, wait until new connection is created. **Close** the browser tab.

10. Select **Refresh**. Verify the new connection is selected in the drop-down. 

11. Select **Import** and wait for the message **Solution "Data Import" imported successfully** to appear.

12. Select **Publish all customizations** and wait for the publishing to complete. 


#### Task 2: Review and run flow

1.  Open the **Data Import** solution you imported.

2.  Select the **Import Data** flow. 
 
3.  If necessary, dismiss the welcome prompt by selecting **Get started**.

4.  Select **Edit** from the Command Bar.

5.  Expand the **InputData** step.

6.  Review the JSON text in the **Value** field. This is the data that will be imported into your environment. Note: The image data is encoded as Base-64 text.

7.  Expand the **EachDepartment** for each control.

8.  Expand and review the **Upsert Department** step.

9. Expand and review the rest of the steps.

10. Select **Save** to save the flow.

11. Select the **🡠** back button to go back to the previous page.

    ![A Screenshot with an arrow pointing to the arrow icon to go back](02-1/media/image92(1).png)

12. Open the **Import Data** flow **Details** and select **Run**.

    >**Note:** If the **Run** option is disabled then make sure the flow has been enabled by selecting **Turn on**.

14. Select **Run flow**.

15. Select **Done**.

16. Wait for the flow run to complete. Select the **Refresh Flow runs** button to check if the flow run completes successfully.

    ![A Screenshot with an arrow pointing to the refresh button in the top right corner and a border around the status showing it has succeeded](02-1/media/image93(1).png)

17. Close the flow editor browser window or tab.

18. Select **Done** on the popup, if prompted.


#### Task 3: Review imported data

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) and make sure you are in the correct environment.

2.  Select **Apps** and open the **Company 311 Admin** model-driven application.

3.  Select **Problem Reports**. You should see new rows of data.

    ![A screenshot with a border around problem new reports rows.](02-1/media/image104(1).png)

    >**Note:** Because the input status reason is picked randomly, some of the imported problem report rows may have the status reason of Completed, Won't Fix, or Inactive. Select the **Resolved Problems** view to find these rows.

4.  Open one of the **Problem Report** Rows.

5.  Select the **Search** icon of the **Building** lookup and make sure building Rows were imported.

    ![A screenshot of a border around the building lookup with the building rows imported](02-1/media/image95(1).png)

6.  Scroll down and select the **Department** lookup.

7.  Make sure the department Rows got imported.


### **Bonus exercise**

  - Deal with problem report assignment within a department.

