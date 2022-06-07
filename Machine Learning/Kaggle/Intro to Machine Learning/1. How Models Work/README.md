# How Models Work?

Created: June 6, 2022 2:48 PM
Module: 1
URL: https://www.kaggle.com/code/dansbecker/how-models-work

# Introduction

- Predicting a value based on values seen previously, and using those patterns to make new predictions
- We will start with a model called ***Decision Tree***
    - There are other fancy models that give more accurate predictions
    - Decision trees are easy to understand
    - Decision trees are the basic building block for some of the best models in Data Science

### Simplest possible ***Decision Tree***

![https://i.imgur.com/7tsb5b1.png](https://i.imgur.com/7tsb5b1.png)

- It divides houses into 2 categories
    - The predicted price for any house under consideration is the historical average price of houses in the same category
- We use the data to decide how to break the houses into two groups
    - Then determine the predicted price of each group
- **Fitting / Training the model** → Capturing patterns from data
- The data which is used to ***fit*** the model is called **training data**
- After the model has been fit, we can apply it to new data to **predict** prices of additional homes

### Improving the Decision Tree

Since the model does not capture most factors affecting house prices, like number of bathrooms, lot size, location, etc

- We can capture more factors using a tree that has more *splits*
- These are called *deeper trees*

![https://i.imgur.com/R3ywQsR.png](https://i.imgur.com/R3ywQsR.png)

- Predict the price of any house by tracing through the decision tree, picking the path corresponding to that house’s characteristics
- Predicted price of the house is at the bottom of the tree
- **Leaf** → Point at the bottom where we make a prediction