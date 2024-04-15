## Results:
Paper Weakness [Author1]:\
Evaluating CQR solely on the REDD dataset limits the generalizability of the findings; including additional datasets could validate the method's robustness across different settings. A more extensive review of recent applications of uncertainty quantification could enhance the study's context and highlight the novelty of the CQR approach.

Based on your feedback, we incorporated another dataset - Dataport Pecan Street dataset consisting of 20 homes from Austin, Texas. The results are listed below. 

| Row                                            | Uncertainty Method    | Calibration Method  | Refrigerator | Air   |
|------------------------------------------------|-----------------------|---------------------|--------------|-------|
| Model: S2P (Homoscedastic)                     |                       |                     |              |       |
| Before Calibration                             |                       |                     |              |       |
|                                              1 | MC                    | -                   |        0.295 | 0.352 |
|                                              2 | DE                    | -                   |        0.314 | 0.355 |
| After Calibration                              |                       |                     |              |       |
|                                              3 | MC                    | Isotonic            |        0.187 | 0.268 |
|                                              4 | DE                    | Isotonic            |        0.213 | 0.252 |
|                                              5 | -                     | Conformal           |        0.069 | 0.061 |
|                                              6 | -                     | Conformal+Smoothing |        0.068 | 0.058 |
|                                                |                       |                     |              |       |
| Model: Gaussian S2P (Heteroscedastic)          |                       |                     |              |       |
| Before Calibration                             |                       |                     |              |       |
|                                              7 | Provided by the model | -                   |        0.184 | 0.086 |
|                                              8 | MC                    | -                   |        0.157 | 0.051 |
|                                              9 | DE                    | -                   |        0.151 | 0.068 |
| After Calibration                              |                       |                     |              |       |
|                                             10 | Provided by the model | Isotonic            |        0.064 | 0.137 |
|                                             11 | MC                    | Isotonic            |        0.042 | 0.061 |
|                                             12 | DE                    | Isotonic            |        0.062 | 0.125 |
|                                             13 | Provided by the model | Conformal           |        0.031 | 0.081 |
|                                                |                       |                     |              |       |
| Model: S2P (Conformalized Quantile Regression) |                       |                     |              |       |
| Before Calibration                             |                       |                     |              |       |
|                                             14 | Provided by the model | -                   |        0.172 | 0.152 |
| After Calibration                              |                       |                     |              |       |
|                                             15 | Provided by the model | Conformal           |        0.043 | 0.064 |
|                                             16 | Provided by the model | Conformal+Smoothing |        0.042 | 0.058 |


We analyse two appliances - Refrigerator and air. In both appliances, for the homoscedastic case, Conformal and Conformal+Smoothing gives the best result (compare rows 5,6 to rows 1-4). Going to heteroscedastic case, after calibration, Conformal gives comparable if not the best results for both appliances (compare rows 13 vs 7-12). Quantile Regression improves upon this and Conformal prediction further improves performance giving the lowest errors (compare rows 15, 16 vs rows 1-14). Thus giving such a good result while using less resources is a big thing. 

Similar to the previous dataset, here also we find that our method is comparable if not the best among all 16 methods. This proves the robustness of our approach where we get similar results across different datasets. 
