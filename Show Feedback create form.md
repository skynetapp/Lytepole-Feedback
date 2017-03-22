#### Date: 27/02/2017

#### Description: This document explains the code flow of Feedback create form.

#### Step 1:

- Function **showFeedbackCreateForm** will be called first from index.php to controller page. when user clicks on add button in feed back it calls this function and this function redirect to the create form of feed back.
- From action page, function **showFeedbackCreateForm** will be redirected to FeedbackView.php which is used to show the feed back create form.
- The above function will be called in tpl page to display the view.
- The tpl page will be **FeedbackCreateForm.tpl** in views folder.
