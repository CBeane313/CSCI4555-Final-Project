# CSCI 4555 Neural Networks and Machine Learning

## Final Project

### Collin B. & Max Q.

#### Learning Outcome

-   Students will be able to design, implement, and train a simple neural network for a given problem and justify their design and parameter choices.

#### Data

-   We will be using steam game data to estimate game ratings
-   Data set can be found [HERE](https://www.kaggle.com/datasets/whigmalwhim/steam-releases/data?select=game_data_all.csv)



###How to run them
Recommend to download the NeuralNetwork.rmd file and the steamGameData.csv from [HERE](https://www.kaggle.com/datasets/whigmalwhim/steam-releases/data?select=game_data_all.csv).
Ensure all the packages at the top of the rmd file are installed. then you should be able to run or knit.

###What data was used and what the model is trying to predict
We use the steam game data and tried to predict the rating(which is rated from 1- 100) for a specific game. 

###Features used and their encoding
we had 3 attempts
attempt 1 uses postivie reviews(numeric), total reviews review(numeric), percentage(numeric) 
attempt 2 and 3 uses all of attempts 1 data and engine type(categorical one hot encoding) and primary genre(categorical one hot encoding) and in attempt 3 we normalized all the numerics used using L1 norm.

###The architecture of the model (number of layers and nodes, functions used, etc.)
attempt 1: input layer is 64 nodes with 3 inputs and activation function of ReLu, one hidden layer of 64 nodes using sigmoid activation, one output node with linear activation.
attempt 2 & 3:input layer is 256 nodes with 112 inputs and activation function of ReLu, one hidden layer of 64 nodes using sigmoid activation, one output node with linear activation.
our loss function for all of the attmepts is MSE and our accuracy function is MAE

###What the project accomplishes and what remains to be done 
the project accomplished our goal of predicting rating at high level of accuracy. we have MAE of .5 with r squared values of .99 and above with loss lower than 1. Possibly if we wanted to add another attempt with more features however we believe the model is to a level that is accurate enough where that wouldn't be necessary. 



### project work write up:

###Description of your design matrix, i.e. what are the features of the data, how the data was obtained (URLs for downloaded data), any preprocessing that you did with the data, and 2-3 sample rows of the design matrix, with explanation. Since your algorithm is supervised, indicate what you are using as label(s). Also mention the number of elements in the dataset. Any other relevant statistical (or other) properties of the data should be mentioned here. 

to obtain the data and run it:
Recommend to download the NeuralNetwork.rmd file and the steamGameData.csv from [HERE](https://www.kaggle.com/datasets/whigmalwhim/steam-releases/data?select=game_data_all.csv).
Ensure all the packages at the top of the rmd file are installed. then you should be able to run or knit.

for pre processing we removed a lot of columns because they wouldn't be useful. we omitted any rows that had NA. after which we extracted the game engine by using regex on the detected technologies column to extract just the engine used. we did a similar thing for the primary genre where we used regex again to just grab the genre name from the primary genre column. we then created another column where each unique engine would have its own categorical value and we did the same for each genre as well and then one hot encoded those values. now for features we keep are: Primary genre, engine, positive reviews, total reviews, negative reviews, rating, and review percentage. 36711 total rows/observation in the data set.   



###Your goals (what you are trying to predict) and your hypotheses.
our goal was to be able to predict the rating of a game which scales from 0-100. our hypothesis was that predict the rating of steam games wouldn't be difficult because rating is heavily influenced by total number of reviews and the percentage of reviews. With knowing that as long as we used that data we should be pretty accurate. 

### Methods: what machine learning system you are using, what kinds of neural networks you are constructing and why. The "why" part is important. 
we used the keras package in R. and we do a feed forward network for a regression task. we choose feed forward neural networks because they are useful for feature learning which is good for regression tasked. It is also flexible to be able to use different activation functions to suit our needs. 

###Description of your training process: how do you select your training data? Your testing data? Validation data, if you have it? 
We did a random split of 75-25 and we don't have validation data. We assumed our data was normally distributed with using the rating because really bad ratings should be as common as really highly ratings and so we went with a random split. 

###Description of your process: what you have tried, what worked, what didn't, what you modified. Models descriptions and probability distributions should be mentioned.
We went with a simple design to start and created a linear model for comparison purposes that used all the features and for our actual first Nueral Network attempt we used total reviews, positive reviews, and review percentage. We had an input layer that is 64 nodes with 3 inputs and activation function of ReLu, one hidden layer of 64 nodes using sigmoid activation and one output node with linear activation. using that structure it was very succesful with a high impressive r squared value. the activation functions we choose worked very well because looking at our data gathered it shows that relu would work well since we had no negatives and for sigmoid worked well because we had rating from 0-100 and sigmoid goes from 0-1 so we could easily scale it up. we tried tanh and it worked but it wasn't as effecient as sigmoid so we stuck with sigmoid.

For our second attempt we used all of attempts 1 data and engine type(categorical one hot encoding) and primary genre(categorical one hot encoding) where we had an input layer that is 256 nodes with 112 inputs and activation function of ReLu, one hidden layer of 64 nodes using sigmoid activation, one output node with linear activation. we increased the amount of nodes used and it seemed to have a good affect on the nueral network. 

for our third attempt it was pretty much the same as the second attempt but we normalized the all the numerics using L1 norm. we choose L1 norm because it is robust against outliers which could be useful in the case where we have a lot of small games that have very little review total and then giant games where they have millions of total reviews. 

###Results: clearly state all the results (specific metrics, such as accuracy, MAE, etc.) on training and testing data. Note that due to issues with the settings I may or may not be able to run your project, so you need to include all of your results. 
we used NAE because it's a regression model and R squared mainly because it's similar to accuracy. and our loss was MSE which is also a good option for a regression model.

attempt one 
Loss = 2.5087 (test)
MAE = 1.17 (test)
R2 = 99.7% (train)


attempt two
Loss = 0.6172 (test)
MAE = 0.54 (test)
R2 = 99.6% (train)

attempt three
Loss* = 6.47 x 10-5 (test)
MAE* = 0.0057 (test)
R2 = 99.8% (train)


###Conclusions: what have you learned about your data? Clearly indicate the basis of your conclusions. 
Predicting the rating isn't that difficult and can be done pretty easily using a simple model as shown that attempt 1 preforms fairly well even when compared to the other 2 attempts as long as you have the review data.

###Challenges; opportunities for improvement.
one challenge we faced was getting the engine and genre data to look the way we wanted and to expirement with different regext to get it to be the way we wished it to be. There aren't many ways to really improve the prediction of rating but it could be more interesting to predict a different metric to predict and wish there were more metrics/columns to use. 
