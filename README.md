Step 1: PreProcess the data

Okay so I successfully removed the EIN and NAME columns, as they provided no value as instructed. I then ran the application_df.nunique print function on the dataframe to see what the number of values were for each column.
That was not difficult, although the Application type and the Classification type stood out immediately as needing to be reduced as the number of values in them was greater than 10, it specifies 9 in the instructions. 
First to go were the application_type values, there were 17, and replaced values that were higher than 528, everything else was grouped into another category and the number of values for that column was 9 unique values when finished.

Next up was the classification count, there were 71 values, and although the starter code specified that maybe looking at values greater than 1 would be helpful, in the end it still left way too many values to keep, it left 45 unique values.
So I decided to keep the 9 values that were used in the application type, and grouped the rest into another category, so greater than 194, actually greater than 190 was specified as the classifications to replace value. I then ran the one hot encoder, merged it with the original application df,
and then dropped the originals that weren't numerical.

I decided on the application Is Successful for the features and target arrays, and there was no issue with the standard scalar instance.

Forgot to call the 5 period frequency for the fit statement, and so updated the starter code to accommodate the specification, got it to print and reuploaded.


Step 2: Comppile, Train and Evaluate the Model

The number of input features was left as the len(X_train[0]), the number of hidden nodes of the first hidden layer was decided to be 8, using a relu activation function. The number of layers for the second hidden layer was decided as 5, with a relu again for the activation function.
The output layer was decided to be sigmoid, and the model was selected as 100 epochs, and it never got above 72% so was 3% off from the specified 75%, saved to alphabetsoupchairt.h5

Step 3: Optimize the Model

So to begin with, I utilized Google Colab’s ability to churn through the necessary number of iterations on each of the three attempts, as my first attempt was at 72%. 
I followed the idea of using the different ‘Status’, ‘Is_Successful’ as the two binary functions. With ‘Status’, in attempt One, the values were reshaped to (-1, 1) and the number of hidden nodes for each of the two hidden layers were 7, and 8 respectively, with relu, relu and sigmoid as the three activation functions. 
This churned out a 99.987% accuracy over 100 epochs, and when fitted to the model, it achieved 100% accuracy of the same number of epochs, with the activation function of ‘relu’ with 9 units in the first layer and 8 units in the second being the optimal build. 

That achieved, I decided to change the activation function for the second and third attempts. 
I began by attempting to see what the output of the 4 functions we had used in class were , relu, tahn, sigmoid and linear with mixed success. 
In this I attempted to decrease the number binned variables, keeping the ‘application type’ at 9 values, the classification type at 9 values, and the Ask_Amount, down from 8747 values into bins of 5,000, 10,000, 25,000, 100,000, 500,000, 1 Million, 5 Million, and greater than 50+ Million. 
This increased the number of values to 55, and the activation for this attempt was set at Is Successful. This Ask Amount overwrote the original Ask Amount with the new binned values, reducing  the number to 9 again. Even with the optimal increase in the number of epochs to 200, this  failed to break higher than the 73% of the pre-attempt. 
There were 4 hidden layers, an increase of two over previous attempts but the first two were the only variables of consequence with 7 in the first and 9 in the second, the remaining were left at 1 value. And all were specified as the activation functions as sigmoid.

The final attempt kept the bins of Ask Amount, decreased the number of Classifications to 6, the Application Type was decreased to 6 as well. 
Is Successful as the other binary function was again used, with an attempt of two relu and three sigmoid layers, respectively in that order. 
The number of values was decreased to some 50 columns, and the number of epochs was decreased to 150. 
This unfortunately only achieved a 73.3% accuracy, as every other column had already been categorized, the models two targets, and the number of values that I was binning was decreasing the number of overall features but retaining the jist of what the columns represented there wasn’t really anything to be gained by decreasing further. 

Step 4: Write a Report on the Neural Network Model

I selected 7, and 8 neurons for the first attempt, 7, 7, 1 and 1 for the second attempt and 7, 9, 1, 1, and 1 for the third attempt. 
I did not wish to increase the number of neurons beyond 8 for the most part, per our instructors’ specifications. I was able to achieve the target performance using the Status column, but not with the Is Successful column. 
Overall there was a mix of changes to the number of hidden layers, the number of epochs ranged from 100, 200, and 150; the number of variables, was changed both by increasing and decreasing the number of values, unfortunately over many cycles beyond the three documented here, 
The accuracy with Is Successful never broke through the 73% threshold that it hovered around, but if the Status was called as the feature then the model would quickly achieve 100% accuracy.

