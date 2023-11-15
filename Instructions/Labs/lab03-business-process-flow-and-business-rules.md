# Course Introduction
 
> -  Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)

# Lab 02.2: Business Process Flows and Business Rules

## Lab Scenario

In this lab you will enhance the data model and improve the app behavior by adding a business process flow and a business rule.

## Lab Objectives

- Exercise 1 : Create BPF lifecycle of problem report
- Exercise 2 : Business rule to not allow close without resolution

## Prerequisites

* Must have completed **Lab 02.1: Data model and model-driven app**

### Exercise 1: Create business process flow

In this exercise, you will create a business process flow for the problem report table.

#### Task 1: Customize Table

In this task, you will add a lookup Column to the problem report table.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Locate and open the **Problem Report** table. 

4.  Select **+ New**, then select **Column**. 

5.  Enter `Assign to` for **Display name**, select **Lookup** for **Data type**, select **User** for **Related table**, and select **Save**.

    ![A screenshot of the column properties panel for Assign To column with all relevant values in each field](02-2/media/image1(1).png)

6.  Select **All** in the **Objects** navigation tree.

7.  Select **Publish all customizations** and wait for the publishing to complete.


#### Task 2: Create business process flow

In this task, you will create a business process flow for the Problem Report table.

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Select **+ New > Automation > Process > Business process flow**.

    ![image-20221004145025636](02-2/media/image2(1).png)

4.  In the **New business process flow** panel, enter `Problem resolution process` for **Display name**, select **Problem Report** for **Table**, and select **Create**.

    ![A screenshot of New business process flow panel with relevant field values.](02-2/media/image3(1).png)

5.  Open the **Problem resolution process** Business Process flow created in the previous step. Select the **New stage**, go to the **Properties** pane, change the **Display Name** to `Route` and select **Apply**. 

    ![A screenshot of the new stage and properties pane](02-2/media/image4(1).png)

6.  Expand **Details** of the **Route** stage.

    ![A Screenshot with an arrow pointing to the details button](02-2/media/image5(1).png)

7.  Select **Data Step \#1**, go to the **Properties** pane, select **Building** for **Data Field**, and select **Apply**.

    ![A screenshot of the new stage with data step one selected and the properties pane open](02-2/media/image6(1).png)

8.  Select **+ Add** and select **Add Data Step**.

    ![A Screenshot with an arrow pointing to the add button and a border around add data step button](02-2/media/image7(1).png)

9.  Select the **+** option to add the data step below the **Building** data step.

    ![A screenshot of a data step being about to be added to the process stage](02-2/media/image27(1).png)

10. Select the new data step, go to the **Properties** pane, select **Location** for **Data Field**, and select **Apply**.

11. Select **+ Add** again and select **Add Data Step**.

12. Select the new data step, go to the **Properties** pane, select **Department** for **Data Field**, and select **Apply**.

13. The **Route** stage should now look like the image below.

    ![A screenshot of the completed route stage with three data steps: building, location, and department](02-2/media/image8(1).png)

14. Select **+ Add** and select **Add Stage**.

15. Add the new stage after the **Route** stage.

    ![A screenshot of the completed route stage with three data steps: building, location, and department](02-2/media/lab03-ex1-t2-s15.png)

16. Select the stage, go to the **Properties** pane, enter `Fix` for **Display Name**, and select **Apply**.

17. Expand **Details** of the **Fix** stage.

18. Select **Data Step \#1** of the **Fix** stage.

19. Go to the **Properties** pane, select **Assign to** for **Data Field** and select **Apply**.

20. Select **+ Add** and select **Add Stage**.

21. Add the new stage after the **Fix** stage.

22. Select the new stage, go to the **Properties** pane, enter `Resolve` for **Display Name** and select **Apply**.

23. Expand **Details** of the **Resolve** stage.

24. Select **Data Step \#1** of the **Resolve** stage.

25. Go to the **Properties** pane, select **Resolution** for **Data Field** and select **Apply**.

26. Select **+ Add** and select **Add Data Step**.

27. Add the new data step below the **Resolution** data step.

28. Select the new data step, go to the **Properties** pane, select **Resolved on** for **Data Field** and select **Apply**.

29. The Business process flow should now look like the image below. Select **Save**.

    ![A screenshot of a Business Process Designer with an arrow pointing to the save button](02-2/media/lab03-ex1-t2-s29.png)

30. Select **Activate**.

    ![A screenshot of a Business Process Designer with an arrow pointing to the save button](02-2/media/lab03-ex1-t2-s30.png)

32. Select **Activate** again on the pop-up.

33. Confirm that Status: **Active** shows at the bottom left of the Business Process Flow canvas.

    ![A screeshot of a high-level overview of a business process with the words "Status: Active" highlighted in the left bottom corner](02-2/media/image28(1).png)

34. Close the process editor browser window or tab.

35. Select **Done**.


### Exercise 2: Create business rule

In this exercise, you will create a business rule that will block completion of problems without resolution.

#### Task 1: Create business rule

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Solutions** and open the **Company 311** solution.

3.  Locate and open the **Problem Report** Table.

4.  Select **+ New** and under **Customizations**, select **Business rule**.

5.  Make sure the **Scope** is set to **Entity** in the selector in the right corner of the screen.

    ![A screenshot of the rules panel](02-2/media/lab03-ex2-t1-s5.png)

7.  Select the **Show details** chevron located next to New business rule title on the same row as the scope.

    ![A Screenshot with an arrow pointing to the drop down icon next to the text problem report: new business rule and a border around the scope set to entity on the right hand side of the page](02-2/media/lab03-ex2-t1-s7.png)

6.  Change **Business rule name** to `Completion rule` and select the **Hide details** chevron.

    ![A screenshot of a business rules property pane with an arrow pointing to the shevron that collapses the entire property pane](02-2/media/lab03-ex2-t1-s6.png)
 
7.  Select the **Condition**.

8.  Go to the **Properties** pane and change the **Display Name** to `Resolution required`

9.  Scroll down the **Rules** section, select **Status Reason** for **Field**, select **Equals** for **Operator**, select **Value** for **Type**, select **Completed** for **Value**, and select **Apply**.

    ![A screenshot of the rules panel](02-2/media/image14(1).png)

10. Select **+ New**.

    ![A Screenshot with an arrow pointing to the new button](02-2/media/image15(1).png)

11. Scroll down to **Rule 2**, select **Resolution** for **Field**, select **Does not contain data** for **Operator**, make sure **AND** is selected for **Rule Logic**, and select **Apply**.

    ![A screenshot of the rules panel if you scroll further down with the relevant text in each field](02-2/media/image16(1).png)

12. Select **+ Add**.

    ![A Screenshot with an arrow pointing to the add button](02-2/media/image17(1).png)

13. Select **Add Show Error Message**.

14. Add the action on the **true** path of the condition, indicated by the tick.

    ![A Screenshot with an arrow pointing to the add button on the true path of the condition](02-2/media/image18(1).png)

15. Select the new action, go to the **Properties** pane, enter **Show message** for **Display Name**, select **Status Reason** for **Field**, enter `The Problem must have a resolution before it can be closed.` for **Message**, and select **Apply**.

    ![A screenshot of the properties panel with the relevant text in the fields](02-2/media/image19(1).png)

16. The business rule should now look like the image below. Select **Save**.

    ![A Screenshot with an arrow pointing to the save button](02-2/media/image20(1).png)

17. Select **Activate**.

18. Select **Activate** again on the pop-up.

19. Confirm activation. The **Activate** button will change to **Deactivate** and it will show **Activated** in the bottom left of the Business Rule canvas.

20. Close the process editor browser window or tab.

21. Select **Done**.

22.  Select **All** in the **Objects** navigation tree.

23.  Select **Publish all customizations** and wait for the publishing to complete.


### Exercise 3: Test processes

In this exercise, you will test the business process flow and the business rule you created.

#### Task 1: Test processes

1.  Navigate to the [Power Apps maker portal](https://make.powerapps.com/) page and make sure you are in the correct environment.

2.  Select **Apps** and open the **Company 311 Admin** application.

    ![A Screenshot with an arrow pointing to the company 311 admin option in apps](02-2/media/image21(1).png)

3.  Select **Problem Reports** and select **+ New**.

4.  You should see the business process flow stages. Enter `Dark parking lot` for **Title**, select **London Paddington** for **Building**, enter `There are no lights at the north end of the parking lot` for **Details**, and select **Save**.

    ![A screenshot of the new problem report](02-2/media/image22(1).png)

5.  Select the **Route** stage.

    ![A Screenshot with an arrow pointing to the route stage at the top of the page](02-2/media/image23(1).png)

6.  Enter `North-end` for **Location**, select **Maintenance** for **Department** and select the **Next stage** button.

    > **NOTE**
    >
    > If the **Next Stage** button is not visible, then refresh the page.

    ![A screenshot of the drop down from the route stage with the relevant options selected and entered](02-2/media/image24(1).png)

7.  Select a user for **Assign to** and select **Next Stage**.

8.  Select an appropriate date and time for the **Resolved on** and leave the **Resolution** value empty.

9.  Scroll down to the **Resolution details** section and select **Completed** for **Status Reason**. You should see the business rule error message defined earlier.

    ![A screenshot of the error message under status reason](02-2/media/image25(1).png)

10. Enter `Installed lights on the North-end of the parking lot` for **Resolution**. The error message should go away.

    ![A screenshot of the form without the error message after resolution](02-2/media/image26(1).png)

11. Select **Save** to save the Problem Report.
