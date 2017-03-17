#### Step 1:

Function **controlFeedbackDetailViewFlow** takes the inputs from the user, when user clicks on feedback arrow button in feedback list it shows the detail view of the select feed back based on the record id.

- In action, function **createFeedbackListInputVO** takes the inputs array and send to data file and prepares the list object to get the feed back list. Its pepare the input to feed back wsdl
- we will call the user id by calling the function **getUserID()** and append to input array. 
- The input array will be next passed to Function **createFeedbackListInputVO** in **FeedbackData.php** which gets the values from input array and sets the values for list value object to pass for WSDL call. It prepare the query and required input for get_entry_list function to get the feedback list.


#### Step 2:

- Function **getFeedbackList** is used to call the wsdl call for getting the feedback list.
- In action, first wsdl client connection will be set by function **setWSDLHandle**.
- Function **getListArray** in FeedbackWS.php is used send data to wsdl for getting the feedback list array using the **get_entry_list**.
- Result returns the feedback list to controller.

#### Step 3:

- Function **createFeedbackListDataObjectArr** creates a list object array for the data get from wsdl and passes to view page.
- In action, function **createFeedbackListDataObject** will be called from FeedbackData.php gets the values from input array and sets the values for list data object to pass to the view of feedback list form or feedback details page.
- Result returns the feedback list data object array to controller.

#### Step 4:

- Function **showFeedbackDetailView** takes the list data object and gives to the feed back view to disply the feed back detail view.
- In action, function **showFeedbackDetailView** will be called from FeedbackView.php which is used to assign the variables for tpl page and assign the value odject array to varable and redirect to feedback detail view form tpl page.
- The display tpl page will be **FeedbackDetailView.tpl** in views folder.
