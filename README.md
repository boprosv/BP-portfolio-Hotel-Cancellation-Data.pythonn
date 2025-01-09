# BP-portfolio-Hotel-Cancellation-Data.python

In this project, I used a hotel cancellation data CSV file with 36K bookings from Kaggle (https://www.kaggle.com/datasets/youssefaboelwafa/hotel-booking-cancellation-prediction/data). I have attached a raw copy in .ipynb format if you would like to run the code.
Business Problem: 30% of Reservations have been cancelled.
The Project:

To start, I downloaded all the necessary libraries for my analysis. The dataset was clean, and not much needed to be done to prepare the data, just some checkups.

![Screenshot 2024-07-15 125518](https://github.com/user-attachments/assets/9b2788ee-70ff-464f-a561-4129408df434)

Then we executed some Exploratory Data Analysis (not showing all of it):

Price Average:

![Screenshot 2024-04-08 112518](https://github.com/user-attachments/assets/160ec2cf-1e91-4c7b-803f-80d752a2b14e)

Price/Lead time Ratio:

![Screenshot 2024-04-08 112937](https://github.com/user-attachments/assets/635ef72a-f14f-44e3-b37e-fe64aabea8d2)

Cancelled/Not cancelled bookings:

![Screenshot 2024-04-08 114001](https://github.com/user-attachments/assets/e5eeb69a-620a-4ab9-a315-d273f4aeac40)

And:

![Screenshot 2024-07-15 131156](https://github.com/user-attachments/assets/01de5657-765e-4231-a513-03f1cd5b6b30)


Here we can see that almost 30% of bookings were cancelled, so the hotel management needs to develop a strategy to retain clients and reduce cancellations to increase revenue. Reducing cancellations is one of the top challenges in the hotel business. Over two years, 11,889 bookings were cancelled at an average price of $100, resulting in $1,188,900 of lost revenue. Our next step is to address this issue using one of the top tools in the business: XGBoost. The 'golden egg' here is the predicted probabilities for the cancellation list!

![Screenshot 2024-07-15 132351](https://github.com/user-attachments/assets/e0a55ba2-010b-4bde-ae17-0ddfbbde6398)
![Screenshot 2024-07-15 132433](https://github.com/user-attachments/assets/eaf72805-3911-400b-bb28-2265d274017a)


![Screenshot 2024-07-15 132021](https://github.com/user-attachments/assets/6fbf7d24-d14c-4f90-ab2c-b9ef4c040f5e)


Pretty good performance! Now we have a list of all the probabilities of cancelled bookings!

![Screenshot 2024-07-15 133646](https://github.com/user-attachments/assets/0b8a3e9e-a7e3-4aa2-bc0d-21c25bd4ec5c)

Now wanted to run CatBoost and see wich model performs better:

![Screenshot 2024-07-15 134041](https://github.com/user-attachments/assets/0e469d94-c003-48e9-bc4f-fa71df6ab799)
![Screenshot 2024-07-15 134128](https://github.com/user-attachments/assets/abf69ccd-276f-468c-b89d-05f3c01c1464)

XGBoost slightly outperforms CatBoost in this setting.

With the list of cancellation probabilities, the hotel management can decide where the marketing department should concentrate their efforts and which lost customers they have a better chance of reengaging. Additionally, the budgeting department will have a better idea of the numbers to calculate if applied discounts and offers become the strategy for bringing customers back. Now we can run the whole dataset through our model and add the cancellation probability at the end as a new column:

![Screenshot 2024-07-15 140555](https://github.com/user-attachments/assets/4bc2a061-b95d-4c82-a9ae-55d35fb040b3)
![Screenshot 2024-07-15 140633](https://github.com/user-attachments/assets/809d7c69-8e99-47d0-aeba-91b7dcb7b95d)

The next step would be to build an app where, upon a reservation being made and the cancellation probability number updated, the appropriate department can receive the necessary information and take required actions (e.g., promotions, discounts) in line with established policies.


