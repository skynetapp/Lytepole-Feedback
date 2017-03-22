#### Date: 27/02/2017

#### Description: This document explains the code flow of creating Feedback from user.

#### Step 1:

Function **controlFeedbackCreateFlow** will be called first from index.php to controller page which takes the inputs from the user. when user enters data in feed back new create form and click on save, this function will call and using the wsdl it will create the new feed back and set relation with the login user account.

- If the login session is not null, the function **createAddFeedbackInputVO** from controller page will be redirected to action page which takes the input data and prepares the input value object for creating a new feed back.
- Input parameters are Module Name = Feedback and Action Name = FeedbackList.
- In action page, First we will get the user id and append to input data by function **getUserID**.
- From action page, function **createAddFeedbackInputVO** will be redirected to FeedbackData.php which will be creating feedback list array to create new feedback based and given parameters.
- Result returns the list array for create feedback to controller.

#### Step 2:

- Function **createFeedback** from controller page and will be redirected to action page which takes the input value object and passes to the wsdl call to create a new feed back.
- In action page, first wsdl client connection will be set by function **setWSDLHandle**.
- From action page, Function **createNewFeedback** will be redirected to FeedbackWS.php is used to create a new feed back and set relation with account using the wsdl calls(set_entry, set_relationship).
- Result returns the feedback id to controller page and header location will be redirected to feedback list view.
