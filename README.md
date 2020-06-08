# COVID-19 Machine Learning Curve Prediction
## Created by Gavin Uhran
### Description
Finding it difficult to view accurate data on COVID-19? I made a data visualization that allows the user to see the change in COVID-19 cases in Illinois by day. The goal is to help people visualize the 'curve' of cases, observe the peak, and see how our society's mitigation efforts are making a difference! All data is from the Illinois Department of Public Health. For more information, refer to https://www.dph.illinois.gov/covid19/covid19-statistics.
### How it Works
The program first imports the raw **JSON** data from the Illinois Department of Public Health, then creates a **pandas** data frame containing the number of days since the first COVID-19 case in Illinois (x-value) and the change in the number of cases (y-value) in Illinois each day. 

Next, the program scales both the x and y-values between 0 and 1. This helps the machine learning model respond to each epochs mean-squared error (MSE) with less extremity, as it notices less variation in the data. 

The program then begins to build its machine learning model. This is done using the **tensorflow.keras** python library. The program is built on the user's desired learning rate. For simplicity, this model only uses one Sequential layer. Using **sklearn.preprocessing**, the model is given the goal of making a polynomial, with a degree up to 4, that best matches the data. The program then begins to train on the existing data, using the user's inputs for the number of epochs to run and the batch size. Following training, the history of MSE in each epoch is saved.

Finally, the program graphs the history of the MSE vs each epoch run, displaying the number of epochs that the model ran before nearing the endpoint of its training. The program also displays a graph of the original data, with the predicted curve overlaying the data.

### Future Improvements
Moving forward, I would like to improve the final graph the program displays. Currently, the graph still displays the scaled data, with values between 0.0 and 1.0. Ideally, the graph would display the raw data on the y-axis, as well as the actual date on the x-axis. 