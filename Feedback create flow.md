#### Step 1:

Function **controlFeedbackCreateFlow** will be called first from index.php to controller which takes the inputs from the user, when user enters data in feed bacck new create form and click on save this function will call and using the wsdl it will create the new feed back and set relation with the login user account.

- First we will get the user id and append to input data by function **getUserID**.
- If the login session is not null, the function **createAddFeedbackInputVO** takes the input data and prepares the input value object for creating a new feed back.
- In action, function **createAddFeedbackInputVO** will be creating feedback list array to create new feedback based and given parameters.
- Result returns the list array for create feedback.

#### Step 2:

- Function **createFeedback** takes the input value object and passes to the wsdl call to create a new feed back
