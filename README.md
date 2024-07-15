# BP-portfolio-Hotel-Cancellation-Data.python

In this project I used a Hotel Cancellation Data CSV format file with 36K bookings from Kaggle (https://www.kaggle.com/datasets/youssefaboelwafa/hotel-booking-cancellation-prediction/data)
I have attuched a RAW copy in .ipynb format if you would like to run the code.

The project:

To start, I downloaded all the needed libraries for what I wanted to do, the dataset was clean and not much needed to be done to prepare the data, just some checkups.

![Screenshot 2024-07-15 125518](https://github.com/user-attachments/assets/9b2788ee-70ff-464f-a561-4129408df434)

Then executed some Exploratory Data Analysis (Not showing all of them):

Price Average:

![Screenshot 2024-04-08 112518](https://github.com/user-attachments/assets/160ec2cf-1e91-4c7b-803f-80d752a2b14e)

Price/Lead time Ratio:

![Screenshot 2024-04-08 112937](https://github.com/user-attachments/assets/635ef72a-f14f-44e3-b37e-fe64aabea8d2)

Cancelled/Not cancelled bookings:

![Screenshot 2024-04-08 114001](https://github.com/user-attachments/assets/e5eeb69a-620a-4ab9-a315-d273f4aeac40)

And:

![Screenshot 2024-07-15 131156](https://github.com/user-attachments/assets/01de5657-765e-4231-a513-03f1cd5b6b30)


Here we can see that almost 30% of bookings were cancelled, so the Hotel management has to work on a strategy of keeping the clients (One of the top problems in the Hotel business!), and reduce that amount to earn more business!In two years 11889 bookings were cancelled at an average price of 100$ is 1,188,900$ of lost revenue. And that's what we are going to do with our next step. For this problem, we are going to implement one of the top tools in the business: XGBoost. The 'Golden Egg' here is the predicted probabilities for the cancellation list!

# Remove the date and Booking_ID columns
booking = booking.drop(columns=['date of reservation', 'Booking_ID'])

# Convert booking.status to numeric (1 for 'Canceled', 0 for 'Not_Canceled')
booking['booking status'] = booking['booking status'].apply(lambda x: 1 if x == 'Canceled' else 0)

# Convert categorical variables to dummy variables
categorical_features = ['room type', 'type of meal', 'market segment type']
booking = pd.get_dummies(booking, columns=categorical_features)

# Split dataset into training and test sets
train_Data, test_Data = train_test_split(booking, test_size=0.2, random_state=123)

# Define X and y for training
X_train = train_Data.drop(columns=['booking status'])
y_train = train_Data['booking status']

X_test = test_Data.drop(columns=['booking status'])
y_test = test_Data['booking status']

# XGBoost parameters
params = {
    'objective': 'binary:logistic',
    'eval_metric': 'auc',   # using AUC as the evaluation metric
    'max_depth': 6,         # maximum depth of trees
    'eta': 0.1,             # learning rate
    'subsample': 0.8,       # subsample ratio of training instances
    'colsample_bytree': 0.8 # subsample ratio of columns when constructing each tree
}

# Number of boosting rounds
num_rounds = 1000

# Create DMatrix objects for XGBoost
dtrain = xgb.DMatrix(data=X_train, label=y_train)
dtest = xgb.DMatrix(data=X_test, label=y_test)

# Train the XGBoost model
xgb_model = xgb.train(
    params=params,
    dtrain=dtrain,
    num_boost_round=num_rounds,
    evals=[(dtrain, 'train'), (dtest, 'eval')],
    early_stopping_rounds=10,   # Stops if no improvement after 10 rounds
    verbose_eval=True            # Print evaluation results
)


