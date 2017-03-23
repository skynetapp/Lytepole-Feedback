#### Date: 27/02/2017

#### Description: This document explains the code flow of Feedback list.

#### Function: controlFeedbackListFlow

- This function takes the inputs from the user. when user clicks on feedback in side bar it will call this function to display the feedback list.
- **Parameters** - Module Name = Feedback and Action Name = FeedbackList

#### Step 1: createFeedbackListInputVO

#### Step 1.1

- Function **createFeedbackListInputVO** redirects to action page which takes the inputs array and send to data file and prepares the list object to get the feed back list.
- Input Parameters will be  Module Name = Feedback and Action Name = FeedbackList
- In action page, we will get the user id by function **getUserID()** and append to input array. 
- Using above input (parameters) it sets the values for list value object to pass for WSDL call. It prepare the query to get the feedback list.

#### Step 1.2

- Result returns the feedback list object array from action page to controller page.
- **Result** - session id, query, order by, max result, user id, user phone.


#### Step 2: getFeedbackList

#### Step 2.1

- Function **getFeedbackList** will be redirected to action page is used to call the wsdl call for getting the feedback list.
- Input parameters are session id,query,order_by,max_result,user_id,user_phone.

#### Step 2.2
- Using above input (parameters) it will send data to wsdl for getting the feedback list array using the **get_entry_list**.
- Result returns the feedback list from action page to controller page.
- **Result** - session id, module name, query, order by, offset, select fields, max results, deleted.

#### Step 3: createFeedbackListDataObjectArr

#### Step 3.1

- Function **createFeedbackListDataObjectArr** will be redirected to action page which creates a list object array for the data get from wsdl and passes to view page.
- Input parameters will be session id, module name, query, max results etc.

#### Step 3.2

- Using above input (parameters) it sets the values for list data object to pass to the view of feedback list form or feedback details page.
- Result returns the feedback list data object array from action page to controller page.
- **Result** - id, name, description, resolution, date entered, offset.

#### Step 4: showFeedbackList

#### Step 4.1

- Function **showFeedbackList** will be redirected to action page which takes the list data object and gives to the feed back view to display the feed back list.
- The result will be redirected to feedback view form which displays the tpl page.



