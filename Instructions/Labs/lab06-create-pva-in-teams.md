# Course Introduction

> - Common Data Service has been renamed to Microsoft Dataverse. [Learn more](https://aka.ms/PAuAppBlog)
> - Some terminology in Microsoft Dataverse has been updated. For example, *entity* is now *table* and *field* is now *column*. [Learn more](https://go.microsoft.com/fwlink/?linkid=2147247)

# Lab 06: Power Virtual Agents in Teams

## Lab Scenario

Your organization is trying to recycle E-waste and decided to schedule a quarterly E-waste pickup service. Facilities department created an Excel file in OneDrive for business and want employees to be able to add their name and information about the item they want to get picked up to the list.

In this exercise, you will create a Power Virtual Agents chatbot that will get the information from users and add them to the pickup list.

## Requirement

- Chatbot should be able to get information about the item.
- Chatbot should be able to get information about the user.
- Chatbot should be able to add the new item to the list.

## Lab Objectives

In this lab, you will complete the following tasks:

- Exercise 1: Create PVA Chatbot
- Exercise 2: Test and publish the Chatbot

### Exercise 1 – Create PVA Chatbot

#### Task 1 - Add Excel file to OneDrive

In this task, you will add an Excel file to your OneDrive for business and add new rows to this file using PVA and Power Automate.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com).

2.  Select the **App launcher (1)** and select **OneDrive (2)**.

    ![A Screenshot with an arrow pointing to the app launcher icon and a box around the Onedrive option in the app launcher](06/media/applauncher.png)

3.  Select **+ Add new (1)** and select **Files upload (2)**.

    ![A screenshot with a box around the files option in the dropdown from the upload button](06/media/filesupload.png)

4.  Browse to the Lab Resources folder, select the **Recycle.xlsx** file, and select Open.

    > **TIP:** The lab resources folder can be found here:`C:\PL100\PL-100-Microsoft-Power-Platform-App-Maker-prod\Instructions\Labs\06\Resources\`

5.  From the left menu, select **My files**, and select the file that you just added.

    ![A Screenshot with an arrow pointing to the recycle.xlsx file](06/media/recyclebin.png)

6.  The file should just have headers. **Close** the file and OneDrive browser tabs.

    ![A screenshot of an excel spreadsheet with four headers in the first row: name, email, location, and description](06/media/ex1-t1-image4.png)


#### Task 2 - Install PVA

In this task, you will install PVA.

1.  Navigate to [Microsoft Teams](https://teams.microsoft.com).

2.  Select **...More added apps (1)**, enter **power virtual (2)**, and select **Power Virtual Agents (3)**.

    ![A Screenshot with an arrow pointing to the ellipsis icon on the left side of the window and a box around the power virtual agents option](06/media/powerapps.png)

3.  Select **Add**. 

4.  Right-click on the **Power Virtual Agents** and select **Pin**. (If the **Power Virtual Agents** menu is not coming on the left menu, then select **... More added apps** and pin it from the recents.)

    ![A Screenshot with an arrow pointing to the power virtual agents icon and a box around the pin button](06/media/powervirtualagents.png)

5.  Do not navigate away from this page.


#### Task 3 - Create Chatbot

In this task, you will create the chatbot.

1.  On the **Microsoft Copilot Studio** page, select **Start now**.

    ![A Screenshot with an arrow pointing to the start now button](06/media/startnow.png)

1.  On the **Create a chatbot**, select the **Green (1)** team you created and select **Continue (2)**.

    ![A Screenshot with an arrow pointing to the start now button](06/media/createacopilot.png)

1.  On the **Create a copilot**, enter **Green Bot (1)** for **Copilot name**, select **English (2)** for language, select any **Copilot theme (3)** of your choice and then select **Create (4)**.

    ![A Screenshot with an arrow pointing to the start now button](06/media/createbot.png)

1. **Wait** for the chatbot to be created.

1. Enter **Hello** in the **Test your Copilot** and select **Send**. 

1.  The chatbot should respond with the default greeting. You will edit this greeting in the next task.

    ![A screenshot with a box around the bot's default greeting reading: "Hi! I'm a virtual agent. I can help with account questions, orders, store information and more. If you'd like to speak to a human agent, let me know at any time. So what can I help you with today?"](06/media/L6E1T3S6.png)

8.  You can show/hide the chatbot by clicking on the chatbot icon located in the bottom left. This will give more room for the authoring canvas.

    ![A Screenshot with an arrow pointing to the hide bot button](06/media/L6E1T3S7.png)

9.  Do not navigate away from this page.


#### Task 4 - Edit greeting

In this task, you will edit the default greeting.

1.  From the left-hand navigation menu, select **Topics (1)** and open the **Greeting (2)** topic.

    ![A Screenshot with an arrow pointing to the greeting topic in the topics menu](06/media/greetingschatbot.png)

2.  Take a look and see the trigger phrases for this topic.

3.  On the authoring canvas go to the first **Message (2)** and replace the message with the text below.

    ```Hi! I'm a virtual agent. I can help you recycle e-waste by posting items to the Upcycle application or add them to the quarterly e-waste pickup list.```

4.  Select **Save (2)**.

    ![A screenshot of the greeting message replaced with the aforementioned text](06/media/message.png)

5.  Select **Test bot** to show the **Test your copilot**.

6.  Enter **Hey** and select **Send**.

7.  The chatbot should now use your updated message. 

    ![A screenshot of the updated bot greeting message](06/media/ex1-t4-image4.png)

8.  Hide the chatbot.

9.  Do not navigate away from this page.


#### Task 5 - Create topic

In this task, you will create a new topic for the chatbot so it can respond to inquiries.

1.  Select **Topics (1)** and select **+ New topic (2) \> From blank (3)**.

    ![A Screenshot with an arrow pointing to the new topic button](06/media/newtopic.png)

1. Close **Trigger phrases (0)** page.

1. Select **Details** to open the Details pane.

1. Enter **Recycle Reuse Reduce** for Name.

1. Select **Trigger phrases**.

1.  Copy the multi-line text below and paste it into **Add phrases** input box.

    ```
    Recycle
    E-waste
    Green
    Add me
    Upcycle
    Reuse
    Reduce
    Recycle list
    ```

    ![A screenshot of multiple trigger phrases entered in Add phrases textbox](06/media/ex1-t5-image2.png)

6.  Select the **+** to add entries for trigger phrases in bulk.

    ![A screenshot of multiple trigger phrases entered in Add phrases textbox](06/media/+.png)

7.  **Close** the Trigger phrases pane.

8.  Select the first message, enter **I can help you with that.** And then select the **+ Add node** button.

    ![A Screenshot with an arrow pointing to the plus icon to add a node](06/media/ex1-t5-image4.png)

9.  Select **Ask a question**.

    ![A Screenshot with an arrow pointing to the ask a question button](06/media/ex1-t5-image5.png)

10.  Enter the text below in the **Ask a question** textbox.

        ```I can add your item to the Upcycle application or to the e-waste pick-up list. What would you like me to do?```

11. Make sure you have **Multiple choice options** selected for Identify, enter **Add to the Upcycle app** for first option and select **+ New option**.

    ![A Screenshot with an arrow pointing to the new option button](06/media/ex1-t5-image6.png)

12. Enter **Add to the pick-up list** as another option. 

13. Select the **Edit variable** icon on the **Save response as** variable. 

    ![A Screenshot with an arrow pointing to the pencil icon in the box under the text save response as](06/media/ex1-t5-image8.png)

14. Change the variable **Name (1)** to `UserOption` and **close (2)** the variable properties pane. 

    ![A Screenshot with an arrow pointing to the cross icon in the top right corner of the pane](06/media/ex1-t5-image9.png)

15. You should now have two conditions following the question. Select the **⋮ (1)** Options button on one of the conditions and select **Delete (2)**. 

    >**Note:** We are deleting one condition because adding an item to the pick-up list and adding an item to the Upcycle application requires similar information. 

    ![A Screenshot with an arrow pointing to the three dots icon and a red box around the delete button](06/media/UserOption.png)

16. Change the second input value in Condition menu to **has value**.

    ![has value - screenshot](06/media/hasvalue.png)

17. Select **+ > Add node** and select **Ask a question**.

18. Enter the text below in the Ask a question textbox.

    ```What is the name of the item?```

19. Select the **Identify** dropdown and select **User's entire response**.

    ![A Screenshot with an arrow pointing to the drop down icon in the identify field and a box around the user's entire response button](06/media/ex1-t5-image10.png)

20. Select the **Edit variable** icon.

    ![A Screenshot with an arrow pointing to the pencil icon in the box under the text save response as](06/media/ex1-t5-image11.png)

21. Change the variable **Name** to `ItemName` and **close** the variable properties pane.

22. Select **+ > Add node** after the question.

23. Select **Ask a question** again.

24. Enter the text below in the Ask a question textbox.

    ```What is the description of this item?```

25. Select the **Identify** dropdown and select **User's entire response** again.

26. Select the **Edit variable** icon again. 

27. Change the variable **Name** to `Description` and **close** the variable properties pane.

28. Select **+ > Add node** after the question.

29. Select **Ask a question** one more time.

30. Enter the text below in the Ask a question textbox.

    ```What is the location of this item?```

31. Select the **Identify** dropdown and select **User's entire response** again.

32. Select the **Edit variable** icon again.

33. Change the variable **Name** to `Location` and **close** the variable properties pane. 

34. The three questions should now look like the image below. Select **Save**.

    ![A Screenshot with an arrow pointing to the save button in the top right corner](06/media/ex1-t5-image12.png)

35. Do not navigate away from this page.


#### Task 6 - Create flow

In this task, you will create a flow that will add the item to the recycle list or to the Upcycle application depending on the user option.

1.  Go to the last question, select **+ > Add node** and select **Call an action**.

    ![A screenshot of a box around the call an action button](06/media/ex1-t6-image1.png)

2.  Select **Create a flow**.

3.  Select **Power Virtual Agents Flow Template**

    ![A screenshot of a box around the power virtual agents flow template option](06/media/powervirtualagentsflowtemplate.png)

4.  Rename the flow `Add item to app or list` (1) and select **+ > Add an input (2)**.

    ![A screenshot of a box around the add item to app or list button and an arrow pointing to the add an input button under power virtual agents](06/media/ex1-t6-image3.png)

5.  Select **Text**.

6.  Enter `User ID` and select **+ > Add an input** again.

    ![A Screenshot with an arrow pointing to the add an input button](06/media/ex1-t6-image4.png)

7.  Select **Text**.

8.  Enter `UserOption` and select **+ > Add an input** one more time.

9.  Select **Text**.

10. Enter `ItemName` and select **+ > Add an input** one more time.

11. Select **Text**.

12. Enter `Description` and select **+ > Add an input** one more time.

13. Select **Text**.

14. Enter `Location`.

15. You should now have **five inputs**.

16. Select **+ Insert a new step** and select **Add an action**.

    ![A Screenshot with an arrow pointing to the plus icon at the bottom of the power virtual agents pane and a box around the add an action button](06/media/ex1-t6-image5.png)

17. Search for `initialize` and select the **Initialize variable** action.

    ![A screenshot with a box around the initialize variable button](06/media/ex1-t6-image6.png)

18. Enter `Response to bot` for Name, select **String** for Type.

19. Select **+ > Add an action**.

    ![A Screenshot with an arrow pointing to the plus icon at the bottom of the initialize variable pane and a box around the add an action button](06/media/ex1-t6-image7.png)

20. Search for `get user profile` and select the **Get user profile (V2)** action from the **Office 365 Users** connector.

    ![A screenshot with a box around the get user profile V2 button](06/media/ex1-t6-image8.png)

21. In **User (UPN)** field and select **User ID** from the Dynamic content pane.

    ![A screenshot with a box around the user ID box in the user UPN field. There is also an arrow pointing to the user ID option in the dynamic content pane](06/media/ex1-t6-image9.png)

22. Select **+ > Add an action**.

23. Search for `condition` and select the **Condition** action from the **Control** connector.

24. Select the first **Choose a value** field and select **UserOption** from the dynamic content pane.

    ![A Screenshot with an arrow pointing to the UserOption in the dynamic content pane. There is also a box around the user option box in the condition pane](06/media/ex1-t6-image10.png)

25. Select **is equal to** and enter **Add to the Upcycle app**.

26. Go to the **if no** branch and select **Add an action**.

    ![A Screenshot with an arrow pointing to the add an action button in the if no window](06/media/ex1-t6-image11.png)

27. Search for `add a row` and select the **Add a row into a table** action from the **Excel Online (Business)** connector.

    ![A screenshot with a box around the add a row into a table button](06/media/ex1-t6-image12.png)

28. Select **OneDrive for Business** for Location, **OneDrive** for Document Library, **Recycle.xlsx** for File and **PickupTable** for table.

29. Select the **Name** field and select **Display Name** from the dynamic content pane.

    ![A screenshot of a box around the display name box in the name field. There is also an arrow pointing to the dynamic content pane and the display name button](06/media/ex1-t6-image13.png)

30. Select the **Email** field and select **Mail** from the dynamic content pane.

31. Select the **Location** field and select the **Location** dynamic content from the Power Virtual Agents step in the dynamic content pane.

    ![A screenshot with a box around the power virtual agents part of the dynamic content pane and an arrow pointing to the location button. There is also a box around the location box in the location field](06/media/ex1-t6-image14.png)

32. Select the **Description** field and select **Description**  from the dynamic content pane.

33. The flow step should now look like the image below. Select **Add an action**.

    ![A Screenshot with an arrow pointing to the add an action button](06/media/ex1-t6-image15.png)

34. Search for `set variable` and select the **Set variable** action from the **Variable** connector. 

35. Select **Response to bot** for name, select the Value field and select **ItemName** from the dynamic content pane. 

    ![A Screenshot with an arrow pointing to the item name option in the dynamic content pane](06/media/ex1-t6-image16.png)

36. Add the text below after the ItemName. 

    ``` was added to the e-waste pick-up list.```

37. Go to the **If yes** branch and select **Add an action**. 

    ![A Screenshot with an arrow pointing to the add an action button](06/media/ex1-t6-image17.png)

38. Search for `add a new row` and select the **Add a new row** action from the **Microsoft Dataverse** connector. 

    ![A screenshot with a box around the add a new row microsoft dataverse button](06/media/ex1-t6-image18.png)

39. Select **Gadgets** for the **Table name**. 

40. Select the **Location** field and select **Location** from the dynamic content pane. 

41. Select the **Name** field and select **ItemName** from the dynamic content pane. 

42. Expand **Show advanced options**. 

    ![A Screenshot with an arrow pointing to the show advanced options button](06/media/ex1-t6-image19.png)

43. Select **Available** for Availability, select the Description field and select **Description** from the dynamic content pane. 

44. Select **Add an action** after the add a new row step. 

45. Search for `set variable` and select the **Set variable** action from the **Variable** connector. 

46. Select **Response to bot** for Name, select the Value field and select **ItemName** from the dynamic content pane.

47. Add the text below after the **ItemName**.

    ``` was added to the Upcycle application.```

48. The two branches of the condition should now look like the image below.

    ![A Screenshot with an arrow pointing to the return values to power virtual agents box beneath the if yes and if no conditions boxed](06/media/ex1-t6-image20.png)

49. Expand the **Return value(s) to Power Virtual Agents** step.

50. Select **+ Add an output**.

51. Select **Text**.

52. Enter **Response**, select the value field, and select **Response to bot** from the dynamic content pane.

    ![A Screenshot with an arrow pointing to the response to bot option in the dynamic content pane under variables](06/media/ex1-t6-image21.png)

53. Select **Save** to save the flow. 

54. Select the back button next to the flow name.

    ![Back to PVA button - screenshot](06/media/L6E1T6S54.png)

55. You should now be back to the bot authoring canvas.

56. Do not navigate away from this page.


#### Task 7 - Call flow 

In this task, you will call the flow as an action from the Power Virtual Agents bot.

1.  Go to the last question, select **+ > Add node** and select **Call an action (1)**.

2.  Select the **Add item to app or list (2)** flow you created.

    ![A Screenshot with an arrow pointing to the add item to app or list button](06/media/L6E1T7S2.png)

3.  Select the **User ID** drop-down field and select **bot.UserId**.

4.  Select the **UserOption** drop-down field and select **UserOption**.

5.  Select the **ItemName** drop-down field and select **ItemName**.

6.  Select the **Description** drop-down field and select **Description**.

7.  Select the **Location** drop-down field and select **Location**.

8.  Select **+ > Add node** and select **Show a message**.

    ![A Screenshot with an arrow pointing to the show a message button](06/media/ex1-t7-image3.png)

9.  Select the **Insert variable** icon and select **Response**.

    ![A Screenshot with an arrow pointing to the insert variable icon and a box around the response button in the drop down](06/media/ex1-t7-image4.png)

10. Select **+ Add node** and select **End with survey**.

11. The end of the bot conversation should look like the image below.

    ![A screenshot of the end of the bot conversation which shows a message command with {x} response in the box and then an end of conversation command connected below](06/media/ex1-t7-image5.png)

12. Select **Save** to save your changes and wait for the bot to be saved.

13. Do not navigate away from this page.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.


### Exercise 2 – Test and publish the bot

#### Task 1 - Test bot

In this task, you will test the bot.

1.  Select **Test your copilot** option on the bottom left side of the screen.

2.  Enter **Recycle** and select **Send**.

3.  The bot should ask you if you want to add the item to the e-waste list or the upcycle application. Select **Add to the Upcycle app**.

    ![A screenshot with a box around the add to the upcycle app](06/media/ex2-t1-image1.png)

4.  The bot should ask you to provide name. Enter **Bot charger** and select **Send**.

5.  The bot should ask you the description of the item. Enter **Universal bot charger** and select **Send**.

6.  The bot should ask you the location of the item. Enter **Building 4 Room A-754** and select **Send**.

7.  The bot should tell you the item was added to the Upcycle application and ask you if your question was answered. Select **Yes**.

    ![A Screenshot with an arrow pointing to the yes button](06/media/ex2-t1-image2.png)

8.  The bot should ask you to rate your experience, give it a rating.

9.  The bot should thank you and ask you if it can help you with anything else. Select **Yes**.

10. Enter **Reuse** and select **Send**.

11. Select **Add to the pick-up list** this time. 

12. The bot should ask you to provide name. Enter **Bad bot charger** and select **Send**. 

13. The bot should ask you the description of the item. Enter **Bad universal bot charger** and select **Send**. 

14. The bot should ask you the location of the item. Enter **Building 4 Room A-754** and select **Send**. 

15. The bot should tell you the item was added to the e-waste pick-up list and ask you if your question was answered. Select **Yes**. 

    ![A Screenshot with an arrow pointing to the yes button](06/media/ex2-t1-image3.png)

16. Rate the bot. 

17. Select **No, thanks**. 

18. The bot should end the conversation. 

19. Select **Teams**. 

    ![A Screenshot with an arrow pointing to the teams icon](06/media/teams.png)

22. Select the **App launcher (1)** and select **OneDrive (2)**. 

    ![A Screenshot with an arrow pointing to the app launcher icon and a box around the onedrive option](06/media/applauncher.png)

23. Open the **Recycle.xlsx** file. 

24. You should see the **Bad universal bot charger** added by the bot. 

    ![Excel table- screenshot](06/media/ex2-t1-image7.png)

25. Close the **Excel file**. 

26. Close **OneDrive**. 

27. You should now be back on the Upcycle application. 

28. Do not navigate away from this page. 


#### Task 2 - Publish and add bot

In this task, you will publish the bot you created.

1. Select the **... (1)** from the left-hand navigation pane, and select **Power Virtual Agents (2)**. 

    ![A Screenshot with an arrow pointing to the power virtual agents icon on the left hand side of the window](06/media/moreapps.png)

2.  Select **Copilots (1)** tab and select the **Green Bot (2)**. 

    ![A Screenshot with an arrow pointing to the green bot button](06/media/greenbot.png)

3.  Select **Publish** from the left navigation. 

    ![A Screenshot with an arrow pointing to the publish button](06/media/publish.png)

4.  Select the **Publish** button. 

5.  Select **Publish** on the pop-up dialogue and wait for the publishing to complete. 

6.  Select **Availability options**. 

7.  Select **Show to my teammates and shared users**. 

    ![A screenshot of a publish pane with a cursor over shaow to my teammates and shared users.](06/media/downladzip.png)

8. Select **Share**. 

9. Select **Apps**. 

    ![A Screenshot with an arrow pointing to the apps icon](06/media/apps.png)

10. Select **Built with Power Platform** and select the **Green Bot** you created. 

    ![A screenshot with a cursor pointing to Green Bot button](06/media/ex2-t2-image7.png)

11. Select **Add**. 

12. The bot should greet you. You may test the bot again. 

### Review
In this lab, you have completed:
- Created PVA Chatbot,
- Tested and published the Chatbot.

### You have successfully completed the lab
