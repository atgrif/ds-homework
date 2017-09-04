# Anne Griffin AirBnB New User Project Design Writeup
This project is from a Kaggle competition that AirBnB hosted two years ago.  They want users to create a model that accurately predicts the first country a new AirBnB user will book their first trip.  The competition can be found here: https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings

### Project Problem and Hypothesis
AirBnB wants to know which country an individual user is most likely to book their first trip in order to serve that user relevant content to reduce the time between first arriving on the site and booking their first trip.  The intent is to use the new user's gender and age, however there are other details about the user, such as how they arrived at the site, we can explore if there is any relationship.  The countries we will be predicting are a part of a finite set of countries that AirBnB has already defined. While both age and gender are the predictors they are interested in, I am predicting that age will be the biggest predictor.  Different phases of life are associated with different levels of financial stability, as well as travel interests (family friendly locations vs places popular for college sprint break).  This break down will be interesting.

### Datasets
The dataset provided is from AirBnB themselves.  
* train_users.csv - the training set of users
* test_users.csv - the test set of users
- id: user id
- date_account_created: the date of account creation
- timestamp_first_active: timestamp of the first activity, note that it can be earlier than date_account_created or date_first_booking because a user can search before signing up
- date_first_booking: date of first booking
- gender
- age
- signup_method
- signup_flow: the page a user came to signup up from
- language: international language preference
- affiliate_channel: what kind of paid marketing
- affiliate_provider: where the marketing is e.g. google, craigslist, other
- first_affiliate_tracked: whats the first marketing the user interacted with before the signing up
- signup_app
- first_device_type
- first_browser
- country_destination: this is the target variable you are to predict
* sessions.csv - web sessions log for users
- user_id: to be joined with the column 'id' in users table
- action
- action_type
- action_detail
- device_type
- secs_elapsed
- countries.csv - summary statistics of destination countries in this dataset and their locations
* age_gender_bkts.csv - summary statistics of users' age group, gender, country of destination
* sample_submission.csv - correct format for submitting your predictions

### Domain knowledge
I am an AirBnB user.  While I'm no longer a "new" user, and this competition ended 2 years ago, I find that AirBnB often recommends things to me that I'm not remotely interested in, and aren't connected to my last 2-3 searches on AirBnB.  Maybe it's intentional based on their current OKRs, however, I'd liked to understand more how the prediction models that drive recommendations on sites like AirBnB work.  This is a multi label classification problem.  Common ways other people attempted to solve this problem was with XGBoost, random forrest, deep learning, k nearest neighbor, and gradient boosting.

### Project Concerns
Fortunately my data set is pretty clean and since this was originally a competition hosted by AirBnB, the data is pretty complete. My biggest concern is not getting too stuck and being able to finish the project on time.  Hoping between the Jupyter notebooks from class and the discussion on Kaggle, I'm able to solve the problem without too many roadblocks.  The model that seems like it is the most successful is one that we don't exactly cover in class.  XGBoost looks like it contains parts of several other models, but is still its own model type.

### Outcomes
The evaluation metric for this competition is NDCG (Normalized discounted cumulative gain) @k where k=5.  AirBnB requested "For every user in the dataset, submission files should contain two columns: id and country. The destination country predictions must be ordered such that the most probable destination country goes first." The closer the NDCG metric is to 1, the more successful the model is.  Very successful would look like a NDCG metric of 0.8 or higher based on the submissions I've seen on the discussion board.
