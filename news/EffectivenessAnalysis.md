---
layout: default
---
# Effectiveness Analysis

Exyst many models that can by applied a one problem, and we need a way to evaluate the effectiveness of each models to determine which model is better to be applied in the problem.
Use only paramiters like acuracy of the model it is not a good way to evaluate a model, so we will saw some ways to evaluate a model.
## Confusion Matrix
First things first we will difene confusion matrix, also known as an error matrix, is a specific table layout that allows visualization of the performance of an algorithm.

|      *       | *                              | True condition   |*                |
|:-------------|:-------------------------------|:-----------------|:----------------|
| *            | Total Population               | PositiveCondition|NegativeCondition|
| Predicted    | Predicted Condition Positive   | True Positive    | False Positive  |
| condition    | Predicted Condition Negative   | False Negative   | True Negative   |

True Positive: You predicted positive and it’s true.

True Negative:You predicted negative and it’s true.

False Positive: You predicted positive and it’s false.

False Negative: You predicted negative and it’s false.

So we can define some ways to evaluate our model.

### Precision

Precision tell us what proportion of positive identifications was actually correct



```R
precision <- function(tp, fp){
  
  precision <- tp/(tp+fp)
  
  return(precision)
}
```

### Recall 
Recal tell us what proportion of actual positives was identified correctly


```R
ecall <- function(tp, fn){
  
  recall <- tp/(tp+fn)
  
  return(recall)
}
```

### F1-Score
F1 score (also F-score or F-measure) is a measure of a test's accuracy. It considers both the precision p and the recall r of the test to compute the score: p is the number of correct positive results divided by the number of all positive results returned by the classifier, and r is the number of correct positive results divided by the number of all samples that should have been identified as positive. The F1 score is the harmonic mean of the precision and recall, where an F1 score reaches its best value at 1 (perfect precision and recall) and worst at 0.


```R
f_measure <- function(tp, fp, fn){
  
  f_measure <- (2*precision(tp,fp)*recall(tp,fn))/(recall(tp,fn) + precision(tp, fp))
  
  return(f_measure)
}
```

Then, we can create a function to join all this functions above


```R

measures <- function(test, pred){
  
  true_positive <- 0
  true_negative <- 0
  false_positive <- 0
  false_negative <- 0
  
  for(i in 1:length(pred)){
    if(test[i] == TRUE && pred[i] == TRUE){
      true_positive <- true_positive + 1
    }else if(test[i] == FALSE && pred[i] == FALSE){
      true_negative <- true_negative + 1
    }else if(test[i] == FALSE && pred[i] == TRUE){
      false_negative <- false_negative + 1
    }else if(test[i] == TRUE && pred[i] == FALSE){
      false_positive <- false_positive + 1
    }
  }
  
  measures <- c(precision(true_positive,false_positive), 
                recall(true_positive,false_negative), 
                f_measure(true_positive,false_positive,false_negative))
  
  return(measures)
}
```
