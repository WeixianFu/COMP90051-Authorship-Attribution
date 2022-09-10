# COMP90051-Authorship-Attribution

## Files position
1. The main approach: Code -> Final.ipynb
2. Optional code files: Code -> Optional -> (Baseline.ipynb, notebook.ipynb)

## Intro
Authorship attribution is a common task to identify the author of a document. In this project, the goal is to determine whether the target author is the author of the testing paper.

## Preprocessing & Feature Engineering
1. Word Pre-Processing by TF-IDF:  Exploratory data analysis found that some keywords occur more often than others. Therefore, TF-IDF (term frequency-inverse document frequency) technique, which is a combination of term frequency and inverse document frequency, is used before training to minimize the variance.  
2. Author PMI: Exploratory data analysis also found that authors tend to work together and the same group of authors often collaborate multiple times. Examples are author 1298, 156 and 1965. Therefore, it is worth considering the association between the authors.
3. Author Conditional Probability: Although PMI can be used to measure the association between variables, the co-occurrence probability P(x, y) between most variables is zero, thus making PMI approaches the negative infinity. Moreover, the relationship between authors cannot be treated as a relationship between variables, since the collaboration between authors is a subjective choice, not a random event. In this way, author conditional probability was used to measure the association between target and coauthors.

## Baseline approach
One author published several papers and these papers often share many keywords. Therefore, a dictionary with the author as the key and the keywords list as the value is created. Prediction was then performed by comparing the test paper’s keywords list to each author’s. The higher the number of matched keywords, the higher the chance of this paper being written by this author. Our baseline approach achieved an AUC score of 0.78. 

## Main approach
### Binary relevance
The binary relevance method simply trains classifiers for each label independently. This suggests that the training can be performed in parallel, which further reduces the training time. 
LinearSVC and logistic regression models have been chosen to be compared, since both are popular models for binary classification tasks. 
### Classifier chain
Classifier chain is a chain of classifiers where the previous class will become a feature for the next class. We investigated the classifier chain approach with only the LinearSVC, because it performed better than logistic regression in the previous approach.

## Future improvement
1. Stratified sampling
2. Ensemble SVM with non-linear kernels
3. State-of-the-art evaluation metrics

