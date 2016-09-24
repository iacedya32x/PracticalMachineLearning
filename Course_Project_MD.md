Executive Summary
-----------------

The goal of this report is to detail an analysis of participants
performing Unilateral Dumbbell Bicepts Curls. Using accelerometers, we
look to predict the way the curls are performed. There are five
different ways (classes) that were examined.

Examining the Data
------------------

The data was examined for data quality. After examination, it was found
that the columns that contained the following terms had mostly blank or
NAs: kurtosis, skewness, max, min, amplitude, var, avg, stddev. These
were removed from the dataset.

The main dataset analyzed contained 19,622 observations. A separate
holdout dataset of 20 observations was used as an out-of-sample set and
was not used in modeling.

Fitting the Models
------------------

The main dataset was split into a training (70% of data) and test set
(30% of data). Each model was first fit to the training set and checked
on the test set. The models used were a decision tree with length = 50,
a linear discriminant analysis, and a quadratic discriminant analysis.

Reasons for selecting/not selecting models to investigate:

-   Usage of a tree allowed for more flexibility in predictions.
-   Linear discriminant analysis was used to investigate linear
    decision boundaries.
-   Quadtratic discriminant analysis was used to investigate more
    non-linear decision boundaries.
-   Random forests were not investigated due to long runtime.

The results on the test set are shown in the **Appendix**.

The decision tree and quadratic discriminant analysis had much stronger
results than the linear discriminant analysis. The decision tree and
quadratic discriminant analysis models are highly flexible and can be
subject to overfitting. To help account for the flexible model fitting,
we checked these models against the testing set that was set aside. The
accuracy, sensitivity, and specificity were all high except for the
linear discriminant analysis. The decision tree results were slightly
more favorable than the quadratic discriminant analysis where the error
rates were both near 10%.

Final Results
-------------

When applying the decision tree results to the 20 observations that were
held out from the modeling, 18 of the 20 observations were correctly
predicted which implies an out-of-sample error of 10%.

Appendix
--------

**FIGURE A - DECISION TREE (LENGTH = 50)**

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction    A    B    C    D    E
    ##          A 1585   80    8   18    2
    ##          B   25  957   53   38   49
    ##          C   26   64  924   42   36
    ##          D   16   16   24  837   22
    ##          E   22   22   17   29  973
    ## 
    ## Overall Statistics
    ##                                           
    ##                Accuracy : 0.8965          
    ##                  95% CI : (0.8885, 0.9042)
    ##     No Information Rate : 0.2845          
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.869           
    ##  Mcnemar's Test P-Value : 1.292e-14       
    ## 
    ## Statistics by Class:
    ## 
    ##                      Class: A Class: B Class: C Class: D Class: E
    ## Sensitivity            0.9468   0.8402   0.9006   0.8683   0.8993
    ## Specificity            0.9744   0.9652   0.9654   0.9841   0.9813
    ## Pos Pred Value         0.9362   0.8529   0.8462   0.9148   0.9153
    ## Neg Pred Value         0.9788   0.9618   0.9787   0.9744   0.9774
    ## Prevalence             0.2845   0.1935   0.1743   0.1638   0.1839
    ## Detection Rate         0.2693   0.1626   0.1570   0.1422   0.1653
    ## Detection Prevalence   0.2877   0.1907   0.1856   0.1555   0.1806
    ## Balanced Accuracy      0.9606   0.9027   0.9330   0.9262   0.9403

**FIGURE B - LINEAR DISCRIMINANT ANALYSIS**

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction    A    B    C    D    E
    ##          A 1347  186  104   59   44
    ##          B   49  723  108   44  159
    ##          C  143  134  667  113   98
    ##          D  125   42  123  712  114
    ##          E   10   54   24   36  667
    ## 
    ## Overall Statistics
    ##                                           
    ##                Accuracy : 0.6994          
    ##                  95% CI : (0.6875, 0.7111)
    ##     No Information Rate : 0.2845          
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.6196          
    ##  Mcnemar's Test P-Value : < 2.2e-16       
    ## 
    ## Statistics by Class:
    ## 
    ##                      Class: A Class: B Class: C Class: D Class: E
    ## Sensitivity            0.8047   0.6348   0.6501   0.7386   0.6165
    ## Specificity            0.9067   0.9241   0.8996   0.9179   0.9742
    ## Pos Pred Value         0.7741   0.6676   0.5775   0.6380   0.8432
    ## Neg Pred Value         0.9211   0.9134   0.9241   0.9472   0.9185
    ## Prevalence             0.2845   0.1935   0.1743   0.1638   0.1839
    ## Detection Rate         0.2289   0.1229   0.1133   0.1210   0.1133
    ## Detection Prevalence   0.2957   0.1840   0.1963   0.1896   0.1344
    ## Balanced Accuracy      0.8557   0.7795   0.7748   0.8282   0.7953

**FIGURE C - QUADRATIC DISCRIMINANT ANALYSIS**

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction    A    B    C    D    E
    ##          A 1573  101    4    5    0
    ##          B   62  930   53    5   33
    ##          C   17   94  959  133   40
    ##          D   12    2    6  807   27
    ##          E   10   12    4   14  982
    ## 
    ## Overall Statistics
    ##                                           
    ##                Accuracy : 0.8923          
    ##                  95% CI : (0.8841, 0.9001)
    ##     No Information Rate : 0.2845          
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.8637          
    ##  Mcnemar's Test P-Value : < 2.2e-16       
    ## 
    ## Statistics by Class:
    ## 
    ##                      Class: A Class: B Class: C Class: D Class: E
    ## Sensitivity            0.9397   0.8165   0.9347   0.8371   0.9076
    ## Specificity            0.9739   0.9678   0.9416   0.9904   0.9917
    ## Pos Pred Value         0.9346   0.8587   0.7715   0.9450   0.9609
    ## Neg Pred Value         0.9760   0.9565   0.9856   0.9688   0.9794
    ## Prevalence             0.2845   0.1935   0.1743   0.1638   0.1839
    ## Detection Rate         0.2673   0.1580   0.1630   0.1371   0.1669
    ## Detection Prevalence   0.2860   0.1840   0.2112   0.1451   0.1737
    ## Balanced Accuracy      0.9568   0.8921   0.9381   0.9138   0.9496
