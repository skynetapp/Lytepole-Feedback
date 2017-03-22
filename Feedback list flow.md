#### Date: 27/02/2017

#### Description: This document explains the code flow of Feedback list.

#### Step 1:

From index.php, Function **controlFeedbackListFlow()** will be called in the controller page which takes the inputs from the user. when user clicks on feedback in side bar it will call this function. From this function we call the wsdl to get the feedback list and displays.

- In the controller page, function **createFeedbackListInputVO** will be redirected to action page -> **FeedbackAction.php** which is included in contoller.
- Function **createFeedbackListInputVO** takes the inputs array and send to data file and prepares the list object to get the feed back list. Its pepare the input to feed back wsdl.
- Input parameters are Module Name = Feedback and Action Name = FeedbackList.
- we will call the user id by calling the function **getUserID()** and append to input array. 
- The input array will be next passed to Function **createFeedbackListInputVO** in **FeedbackData.php** which gets the values from input array and sets the values for list value object to pass for WSDL call. It prepare the query and required input for get_entry_list function to get the feedback list.
- Result returns the feedback list object array.


#### Step 2:

- Function **getFeedbackList** from controller page will be redirected to action page is used to call the wsdl call for getting the feedback list.
- Input parameters are session id,query,order_by,max_result,user_id,user_phone.
- In action page, first wsdl client connection will be set by function **setWSDLHandle**.
- From action page, Function **getListArray** will be redirected to FeedbackWS.php is used send data to wsdl for getting the feedback list array using the **get_entry_list**.
- Result returns the feedback list to controller page.

#### Step 3:

- Function **createFeedbackListDataObjectArr** from controller page will be redirected to action page which creates a list object array for the data get from wsdl and passes to view page.
- Input parameters will be the data getting from wsdl based on input
- From action page, function **createFeedbackListDataObject** will be redirected to FeedbackData.php gets the values from input array and sets the values for list data object to pass to the view of feedback list form or feedback details page.
- Result returns the feedback list data object array to controller page.

#### Step 4:

- Function **showFeedbackList** from controller page and will be redirected to action page which takes the list data object and gives to the feed back view to display the feed back list.
- From action page, function **showFeedbackListView** is redirected to FeedbackView.php which displays the tpl page.
- The result will be redirected to feedback view form.
- The display tpl page will be **FeedbackViewForm** in views folder.


