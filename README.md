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
From index.php,Function **controlFeedbackListFlow()** will be called in the controller page -> **FeedbackController.php**  which controls all the operations.

#### Step 5:


