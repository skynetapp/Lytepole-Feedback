#### Date: 27/02/2017

#### Description: This document explains the code flow of Feedback Module.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | LytepoleWSConnection
Lib | Smarty,nusoap
Modules | Feedback
Views | FeedbackCreateForm, FeedbackDetailView, FeedbackViewForm

#### Step 1: Login to lytepole with your phone number. 

#### Step 2: Go to left menu -> Feedback and the code flows as follows.

#### Step 3:
Based on the url **https://dev2.lytepole.com/web2/5.7/index.php?module=Feedback&action=FeedbackList** check the module name as **Feedback** and action as **FeedbackList** in index.php

#### Step 4: 
From index.php, Function **controlFeedbackListFlow()** will be called in the controller page -> **FeedbackController.php**  which controls all the operations.

#### Step 5:
In the controller, in function **controlFeedbackListFlow()** one of the function will be called **createFeedbackListInputVO** to action as **FeedbackAction.php** which is included in contoller.

#### Step 6:
In Function **createFeedbackListInputVO** , we will pass the user id by calling the function **getUserID()**. The input data will be next passed to Function **createFeedbackListInputVO** in **FeedbackData.php** which will be included in the action.

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

In **FeedbackData.php** we will set the session of user id in function   **createFeedbackListInputVO** and couple of statements will be executed here.

- If query date is empty, latest date will be entered or else the query date will be entered to function **setQueryDate**.
- Based on the search, the query will be executed which matches the result entered in textbox by calling function **setQuery**.
- If the action is **FeedbackDetailView**, based on the record id output will be displayed.
- setting the Maximum results by calling **setMaxResults**.

#### Step 8:





