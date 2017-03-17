#### Date: 27/02/2017

#### Description: This document explains the code flow of creating Feedback from user.

#### Step 1:

Function **controlFeedbackCreateFlow** will be called first from index.php to controller which takes the inputs from the user. when user enters data in feed back new create form and click on save, this function will call and using the wsdl it will create the new feed back and set relation with the login user account.

- First we will get the user id and append to input data by function **getUserID**.
- If the login session is not null, the function **createAddFeedbackInputVO** takes the input data and prepares the input value object for creating a new feed back.
- In action, function **createAddFeedbackInputVO** will be creating feedback list array to create new feedback based and given parameters.
- Result returns the list array for create feedback.

#### Step 2:

- Function **createFeedback** takes the input value object and passes to the wsdl call to create a new feed back.
- In action, first wsdl client connection will be set by function **setWSDLHandle**.
- Function **createNewFeedback** in FeedbackWS.php is used to create a new feed back and set relation with account using the wsdl calls(set_entry, set_relationship).
- Result returns the feedback id and header location will be redirected to feedback list view.
