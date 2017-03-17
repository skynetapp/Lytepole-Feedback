#### Step 1:

- In Function **createFeedbackListInputVO** , we will call the user id by calling the function **getUserID()** and append to input array. - The input array will be next passed to Function **createFeedbackListInputVO** in **FeedbackData.php** which gets the values from input array and sets the values for list value object to pass for WSDL call. It prepare the query and required input for get_entry_list function to get the feedback list.


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
