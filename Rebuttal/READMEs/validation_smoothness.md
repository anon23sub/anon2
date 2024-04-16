## Results
Q. Can you explain the decision-making process behind choosing the standard deviation for the added noise for smoothing? How does this choice affect the model's calibration error? [Reviewer#1 Q1]

We had previously chosen the standard deviation for the added noise based on some initial experiments. However, we agree with the suggestion that there should be a principled way of choosing this. Thus, we now divide the training data into training and validation.  Thus, we have four datasets: training, validation, calibration, and testing. 

![Validation Image](/Rebuttal/Images/val.jpg)

|                                   | Distribution of Errors | Fridge | Dishwasher | Microwave |
|-----------------------------------|------------------------|--------|------------|-----------|
| Performance of Validation dataset | N(0, 0.01)             | 0.0026 |     0.0051 |    0.0068 |
|                                   | N(0, 0.03)             | 0.0027 |      0.005 |     0.006 |
|                                   | N(0, 0.1)              |  0.003 |     0.0117 |    0.0103 |
|                                   | N(0, 0.3)              | 0.0024 |     0.0486 |     0.045 |
|                                   | N(0, 1)                | 0.0096 |      0.135 |     0.126 |
|                                   | N(0, 3)                | 0.0416 |      0.176 |     0.177 |
|                                   | N(0, 10)               | 0.1023 |      0.197 |     0.194 |
| Performance of Test dataset       | Best one               |  0.092 |      0.047 |      0.23 |


We perform validation with performance measured on the validation set and choose that value of standard deviation which gives the lowest calibration error. We then report the calibration errors on test dataset using value of standard deviation from above for smoothing. We try varying values of standard deviation for calibration ranging from 0.01 all the way to 10. The model over here is Conformalized Quantile Regression. 

standard deviation is a hyperparameter; thus, from zero to the optimal value, the calibration error reduces, but after this, the calibration error increases. The effect of the choice of standard deviation is shown in Table 4 in paper.
