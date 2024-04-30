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
attempt 2 and 3 uses all of attempts 1 data and engine type(categorical one hot encoding) and primary genre(categorical one hot encoding) and in attempt 3 we normalized all the numerics used using L2 norm.

###The architecture of the model (number of layers and nodes, functions used, etc.)
attempt 1: input layer is 64 nodes with 3 inputs and activation function of ReLu, one hidden layer of 64 nodes using sigmoid activation, one output node with linear activation.
attempt 2 & 3:input layer is 256 nodes with 112 inputs and activation function of ReLu, one hidden layer of 64 nodes using sigmoid activation, one output node with linear activation.
our loss function for all of the attmepts is MSE and our accuracy function is MAE

###What the project accomplishes and what remains to be done 
the project accomplished our goal of predicting rating at high level of accuracy. we have MAE of .5 with r squared values of .99 and above with loss lower than 1. Possibly if we wanted to add another attempt with more features however we believe the model is to a level that is accurate enough where that wouldn't be necessary. 