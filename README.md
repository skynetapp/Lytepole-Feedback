#### Date: 27/02/2017

#### Description: This document explains the code flow of Feedback from user.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | LytepoleWSConnection
Lib | Smarty,nusoap
Modules | Feedback
Views | FeedbackCreateForm, FeedbackDetailView, FeedbackViewForm

#### Main code flow:

- For WS Call: index.php -> FeedbackController -> FeedbackAction -> FeedbackWS .
- For View: index.php -> controller -> action -> FeedbackView ->tpl page (Views folder)
- To set Data: index.php -> controller -> action -> FeedbackData  

#### Step 1: Login to lytepole with your phone number. 

#### Step 2: Go to left menu -> Feedback and the code flows as follows.

#### Step 3:
Based on the url **https://dev2.lytepole.com/web2/5.7/index.php?module=Feedback&action=FeedbackList** check the module name as **Feedback** and action as **FeedbackList** in index.php

#### Step 4: 
From index.php, Function **controlFeedbackListFlow()** will be called in the controller page -> **FeedbackController.php**  which controls all the operations.

#### Step 5:
In the controller, in function **controlFeedbackListFlow()** one of the function will be called **createFeedbackListInputVO** to action as **FeedbackAction.php** which is included in contoller.

#### Step 6:
In Function **createFeedbackListInputVO** , we will call the user id by calling the function **getUserID()** and append to input array. The input array will be next passed to Function **createFeedbackListInputVO** in **FeedbackData.php** which will be included in the action.

**_Code:_**

```
function createFeedbackListInputVO($input_arr){
        
		$user_id = $this->getUserID();	
		$input_arr['user_id'] = $user_id;
		//print_r($user_id);exit;
        require_once 'FeedbackData.php';
        $contacts_data = new FeedbackData();
        $contacts_list_vo = $contacts_data->createFeedbackListInputVO($input_arr);
		//print_r($meeting_list_vo);		
        return $contacts_list_vo;      
        
    }
 ```
 
#### Step 7:

**FeedbackData.php** will set the data for passing to wsdl calls. Function **createFeedbackListInputVO** gets the values from input array and sets the values for list value object to pass for WSDL calls. Couple of statements will be executed here.

- If query date is empty, latest date will be entered or else the query date will be entered to function **setQueryDate**.
- Based on the search, the query will be executed which matches the result entered in textbox by calling function **setQuery**.
- If the action is **FeedbackDetailView**, based on the record id output will be displayed.
- setting the Maximum results by calling **setMaxResults**. These functions are called from **FeedbackListVo.php** which is included in the main calling function i.e **createFeedbackListInputVO**.

#### Step 8:

- After creating value object with listing parameters, it will be passed to function **getFeedbackList** which is called in action.
- From action lytepole ws connection will be set by function **setWSDLHandle** in FeedbackWS.php and function **getListArray** is used to get the list by ws call **get_entry_list**. 

#### Step 9:

- Next, function **createFeedbackListDataObjectArr** will be called from controller to action and from action, function **createFeedbackListDataObject** will be called in FeedbackData.php where we can set the fields which are needed to display for a feedback.
- After the fields list array is called, it will be passed to function **showFeedbackList** in controller to action, and from action to FeedbackView.php, function **showFeedbackListView** will be called callsthe tpl page **FeedbackViewForm.tpl** to display all feedbacks.

#### Step 10:

For creating a feedback , call the action as **CreateForm** from index.php -> **showFeedbackCreateForm** called in controller.

- Next from controller, the action function will be called **showFeedbackCreateForm** and from action, function **showFeedbackCreateView** will be called in **FeedbackView.php** which is included in action.
- In view function **showFeedbackCreateForm** , we will display the tpl page as **FeedbackCreateForm.tpl**.
- When feedback is entered in the form, the form action calls **CreateFeedback** and function **controlFeedbackCreateFlow** will be called in controller.
- In controller, first it gets the user id and if session of user id is not null function **createAddFeedbackInputVO** will be called in action.
- In action, function **createAddFeedbackInputVO** will be called in **FeedbackData.php** which sets the session and creates a value object with parameters to add a new feedback.
- Those parameters will be passed to function **createFeedback** in controller and called in action.
- Here we will get the ws client connection and function **createNewFeedback** will be called action to FeedbackWS.php.
- In  FeedbackWS.php, we will call the ws **set_entry** and a record will be inserted in sugar under module -> Bugs.
- Next it sets the relationship with ws call **set_relationship** between Accounts and Bugs.
- If the login session is set, it will redirect to Feedback list page or else displays the message as **session not set**.

#### Step 11:

To show the detail feedback, action **FeedbackDetailView** will be called in index.php and function **controlFeedbackDetailViewFlow** will be called from index.php -> controller.
- Function **createFeedbackListInputVO** will execute to create value object with listing parameters.
- Function **getFeedbackList** will get the array in ws call.
- Function **createFeedbackListDataObjectArr** will create the dataobject of meeting list data.
- Function **showFeedbackDetailView** will be called from controller -> action and then from action -> FeedbackView which calls the tpl page to display **FeedbackDetailView.tpl** in views folder.












