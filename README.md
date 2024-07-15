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


Here we can see that almost 30% of bookings were cancelled, so the Hotel management has to work on a strategy of keeping the clients (One of the top problems in the Hotel business!), and reduce that amount to earn more revenue!In two years 11,889 bookings were cancelled at an average price of 100$ is 1,188,900$ of lost revenue. And that's what we are going to do with our next step. For this problem, we are going to implement one of the top tools in the business: XGBoost. The 'Golden Egg' here is the predicted probabilities for the cancellation list!

![Screenshot 2024-07-15 132351](https://github.com/user-attachments/assets/e0a55ba2-010b-4bde-ae17-0ddfbbde6398)
![Screenshot 2024-07-15 132433](https://github.com/user-attachments/assets/eaf72805-3911-400b-bb28-2265d274017a)


![Screenshot 2024-07-15 132021](https://github.com/user-attachments/assets/6fbf7d24-d14c-4f90-ab2c-b9ef4c040f5e)

Pretty good prformance! Now we have a list of all the porobabylities of cancelled bookings!

![Screenshot 2024-07-15 133646](https://github.com/user-attachments/assets/0b8a3e9e-a7e3-4aa2-bc0d-21c25bd4ec5c)
