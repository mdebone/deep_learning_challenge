Step 1: PreProcess the data

Okay so I successfully removed the EIN and NAME columns, as the provided no value as instructed. I then ran the application_df.nunique print function on the dataframe to see what the number of values were for each column.
That was not difficult, although the Application type and the Classification type stood out immediately as needing to be reduced as the number of values in them was greater than 10, it specifies 9 in the instructions. 
First to go were the application_type values, there were 17, and replaced values that were higher than 528, everything else was grouped into an other category and the number of values for that column was 9 unique values when finished.

Next up was the classification count, there were 71 values, and although the starter code specified that maybe looking at values greater than 1 would be helpful, in the end it still left way to many values to keep, it left 45 unique values.
So I decided to keep the 9 values that were used in the application type, and grouped the rest into an other category, so greater than 194, actually greater than 190 was specified as the classifcations to replace value. I then ran the one hot encoder, merged it with the original application df,
and then tropped the originals that weren't numerical.

I decided on the application Is Succesful for the features and target arrays, and there was no issue with the standard scalar instance.

Forgot to call the 5 period frequency for the fit statement, and so updated the starter code to accomidate the specification, got it to print and reuploaded.


Step 2: Comppile, Train and Evaluate the Model

The number of input features was left as the len(X_train[0]), the number of hidden nodes of the first hidden layer was decided to be 8, using a relu activation function. The number of layers for the second hidden layer was decided as 5, with a relu again for the activation function.
The output layer was decided to be sigmoid, and the model was selected as 100 epochs, and it never got above 72% so was 3% off from the specified 75%, saved to alphabetsoupchairt.h5