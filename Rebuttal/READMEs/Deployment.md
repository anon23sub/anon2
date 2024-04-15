Paper Weakness:
No Deployment Details The author did not provide information about the deployment version of their work or any online experiments. If this article is purely theoretical research, it is not recommended to submit it for the applied track.

Q. The article does not provide detailed deployment information. Does this work only remain as a theoretical exploration? [Reviewer#3 Q2]

| Row                                            | Uncertainty Method    | Calibration Method  | Refrigerator | Air   |
|------------------------------------------------|-----------------------|---------------------|--------------|-------|
| Model: S2P (Conformalized Quantile Regression) |                       |                     |              |       |
| Before Calibration                             |                       |                     |              |       |
|                                             14 | Provided by the model | -                   |        0.077 |  0.04 |
| After Calibration                              |                       |                     |              |       |
|                                             15 | Provided by the model | Conformal           |        0.032 | 0.035 |
|                                             16 | Provided by the model | Conformal+Smoothing |        0.031 | 0.035 |

Even here, our method is able to achieve a very good performance (~low Calibration error). Smoothing further helps to make this better. Our approach achieves comparable error rates to state-of-the-art methods while using significantly fewer computational resources and distribution-free techniques, making it accessible for real-world applications.

We deployed our solution in a university campus whose results are below where we test it on our approach. We use ten days of data and disaggregate the mains power into appliances like Fridge and AC. We even collaborated with a research group at IIT Gandhinagar who collected the live energy data and used our disaggregation models on the data to check if our black box integration functionality gives good results. We can hence say that our system is being used to co-optimize thermal confront, indoor air quality, and other factors in actual homes at the IIT Gandhinagar campus.
