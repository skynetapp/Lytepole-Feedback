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

#### Architecture

- After login in lytepole, when user clicks on feedback in side bar it will call function **controlFeedbackListFlow** which calls the wsdl to get the feedback list and displays.
- when user clicks on feedback arrow button in feedback list it shows the detail view of the select feed back based on the record id by calling function **controlFeedbackDetailViewFlow**.
- when user clicks on add button in feed back its call function **showFeedbackCreateForm** which will redirect to the create form of feed back.
- when user enters data in feed bacck new create form and click on save, function **controlFeedbackCreateFlow**  will call and using the wsdl it will create the new feed back and set relation with the login user account.

