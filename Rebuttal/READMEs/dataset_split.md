## Results: 
Q. Would the choices of calibration datasets affect the ECE results in Table 3? I suggested doing something like cross-validation to estimate the robustness of this result. [Reviewer#2 Q3]

Based on your feedback, we performed cross-validation using a dataset split different from the one used before. We show the results for two different splits above where all train and test houses are changed. The final results for each split is displayed in table format below the split. 

1st Split 
| Appliance  | Training House | Testing House |
|------------|----------------|---------------|
| Fridge     | 1,2,3,6        | 5             |
| Dishwasher | 1,2            | 3             |
| Microwave  | 1,2            | 3             |

| Row                                            | Uncertainty Method    | Calibration Method  | Fridge  | Dishwasher  | Microwave |
|------------------------------------------------|-----------------------|---------------------|---------|-------------|-----------|
| Model: S2P (Homoscedastic)                     |                       |                     |         |             |           |
| Before Calibration                             |                       |                     |         |             |           |
|                                              1 | MC                    | -                   |   0.261 |       0.373 |      0.39 |
|                                              2 | DE                    | -                   |    0.25 |       0.257 |     0.362 |
| After Calibration                              |                       |                     |         |             |           |
|                                              3 | MC                    | Isotonic            |   0.253 |       0.317 |     0.334 |
|                                              4 | DE                    | Isotonic            |   0.298 |       0.212 |     0.216 |
|                                              5 | -                     | Conformal           |   0.244 |       0.282 |    0.3853 |
|                                              6 | -                     | Conformal+Smoothing |   0.239 |       0.221 |     0.193 |
|                                                |                       |                     |         |             |           |
| Model: Gaussian S2P (Heteroscedastic)          |                       |                     |         |             |           |
| Before Calibration                             |                       |                     |         |             |           |
|                                              7 | Provided by the model | -                   |    0.22 |       0.133 |     0.139 |
|                                              8 | MC                    | -                   |    0.16 |       0.065 |     0.135 |
|                                              9 | DE                    | -                   |   0.065 |       0.342 |     0.216 |
| After Calibration                              |                       |                     |         |             |           |
|                                             10 | Provided by the model | Isotonic            |   0.183 |       0.324 |     0.144 |
|                                             11 | MC                    | Isotonic            |   0.265 |       0.123 |     0.161 |
|                                             12 | DE                    | Isotonic            |   0.097 |       0.389 |     0.133 |
|                                             13 | Provided by the model | Conformal           |   0.204 |       0.336 |     0.139 |
|                                                |                       |                     |         |             |           |
| Model: S2P (Conformalized Quantile Regression) |                       |                     |         |             |           |
| Before Calibration                             |                       |                     |         |             |           |
|                                             14 | Provided by the model | -                   |   0.185 |       0.101 |     0.384 |
| After Calibration                              |                       |                     |         |             |           |
|                                             15 | Provided by the model | Conformal           |   0.177 |       0.105 |     0.386 |
|                                             16 | Provided by the model | Conformal+Smoothing |   0.174 |       0.102 |     0.218 |

From Table 1, we can conclude that for all appliances, In Homoscedastic Conformal+Smoothing method performs comparable if not best to the other methods (compare row 6 with rows 1-5). For Fridge and Dishwasher, the Heteroscedastic Conformal method performs poorly with respect to other methods (compare row 13 with rows 7-12). This motivates the Conformalized Quantile Regression approach. Note that for Microwave, we get comparable results. In the Quantile Regression model with Conformal+Smoothing method, we get better results which are now comparable with other approaches. 


2nd Split 
| Appliance  | Training House | Testing House |
|------------|----------------|---------------|
| Fridge     | 1,2,5,6        | 3             |
| Dishwasher | 2,3            | 1             |
| Microwave  | 2,3            | 1             |

| Row                                            | Uncertainty Method    | Calibration Method  | Fridge  | Dishwasher  | Microwave |
|------------------------------------------------|-----------------------|---------------------|---------|-------------|-----------|
| Model: S2P (Homoscedastic)                     |                       |                     |         |             |           |
| Before Calibration                             |                       |                     |         |             |           |
|                                              1 | MC                    | -                   |   0.359 |       0.132 |     0.073 |
|                                              2 | DE                    | -                   |   0.319 |       0.363 |     0.076 |
| After Calibration                              |                       |                     |         |             |           |
|                                              3 | MC                    | Isotonic            |    0.32 |        0.01 |     0.069 |
|                                              4 | DE                    | Isotonic            |   0.339 |       0.227 |     0.265 |
|                                              5 | -                     | Conformal           |   0.319 |       0.024 |     0.028 |
|                                              6 | -                     | Conformal+Smoothing |   0.307 |       0.023 |     0.029 |
|                                                |                       |                     |         |             |           |
| Model: Gaussian S2P (Heteroscedastic)          |                       |                     |         |             |           |
| Before Calibration                             |                       |                     |         |             |           |
|                                              7 | Provided by the model | -                   |   0.207 |       0.334 |     0.217 |
|                                              8 | MC                    | -                   |   0.189 |        0.25 |     0.164 |
|                                              9 | DE                    | -                   |   0.177 |       0.307 |     0.279 |
| After Calibration                              |                       |                     |         |             |           |
|                                             10 | Provided by the model | Isotonic            |   0.149 |       0.335 |      0.16 |
|                                             11 | MC                    | Isotonic            |   0.261 |        0.36 |     0.035 |
|                                             12 | DE                    | Isotonic            |   0.179 |       0.299 |     0.176 |
|                                             13 | Provided by the model | Conformal           |   0.194 |       0.338 |     0.168 |
|                                                |                       |                     |         |             |           |
| Model: S2P (Conformalized Quantile Regression) |                       |                     |         |             |           |
| Before Calibration                             |                       |                     |         |             |           |
|                                             14 | Provided by the model | -                   |   0.214 |        0.33 |     0.058 |
| After Calibration                              |                       |                     |         |             |           |
|                                             15 | Provided by the model | Conformal           |   0.211 |       0.334 |     0.049 |
|                                             16 | Provided by the model | Conformal+Smoothing |   0.201 |       0.198 |     0.048 |


From Table 2, Similar to Table 1, we find that in the Homoscedastic case, Conformal + Smoothing method performs comparable if not best to the other methods (compare row 6 with rows 1-5). The heteroscedastic model improves upon the previous method and gives comparable results for Fridge and Dishwasher. In the Microwave, MC Dropout on GMLP (Row 11) is the best. We then apply our approach Conformalized Quantile Regression and achieve comparable results (row 16 vs row 11) using very few resources relative to MC Dropout. For Fridge, the same approach gives similar results to its heteroscedastic case but improves a lot for Dishwasher (compare rows 13 and 16).

The core conclusion from the above two tables is that our approach gives comparable results while being highly computationally efficient. This is the main takeaway from our results. 





