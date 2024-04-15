## Results
Q. Can you explain the decision-making process behind choosing the standard deviation for the added noise for smoothing? How does this choice affect the model's calibration error? [Reviewer#1 Q1]

Standard deviation is a hyperparameter. Initially, for our experiments, we chose to take approximately 0.1 times the mean errors made by a model with a particular method. This choice helps for an optimal correction with not being too less to make no difference to not being too much, which changes the learned errors. 

|                                                                       | Distribution of Errors | Fridge | Dishwasher | Microwave |
|-----------------------------------------------------------------------|------------------------|--------|------------|-----------|
| Performance of Test dataset using Validation dataset for Calibration  | N(0, 0.01)             |  0.055 |      0.056 |     0.226 |
|                                                                       | N(0, 0.03)             |  0.055 |      0.056 |     0.226 |
|                                                                       | N(0, 0.1)              |  0.055 |      0.059 |     0.224 |
|                                                                       | N(0, 0.3)              |  0.054 |       0.07 |     0.214 |
|                                                                       | N(0, 1)                |  0.053 |      0.126 |     0.154 |
|                                                                       | N(0, 3)                |  0.045 |      0.177 |     0.157 |
|                                                                       | N(0, 10)               |  0.067 |      0.181 |      0.18 |
| Performance of Test dataset using Calibration dataset for Calibration | Best one               |  0.082 |      0.047 |     0.145 |


Based on your feedback, we have also performed validation to choose the value of standard deviation. We divide the validation dataset from the training dataset. Thus, it is independent of the calibration dataset. We choose that value of standard deviation which gives the lowest calibration error on the test dataset with the validation dataset used for calibration. Using this, we finalize the value of the standard deviation for each appliance. We then go back to our initial settings and use these values of standard deviation to get the final error (last row). We show our results in the table above. 

We try varying values of standard deviation for the validation dataset ranging from 0.01 all the way to 10. The model over here is Conformalized Quantile Regression. 

This choice affects the model’s calibration error in this manner: till the optimal value of standard deviation, the calibration error reduces, but after this, the errors would change too much, resulting in an increase in calibration error. The effect of the choice of standard deviation is shown in Table 4. For each appliance, this behavior varies. 
