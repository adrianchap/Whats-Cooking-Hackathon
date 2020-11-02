# ![GA Logo](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: What's Cooking?

This study examines a dataset from [yummly](https://www.kaggle.com/c/whats-cooking) that contains almost 40,000 ingredient lists from collected recipes and the region from the cuisine the recipe is from.  The task was to determine if advanced classification methods and NLP techniques could successfully predict the region of a cuisine given its ingredient list.  

# Data Cleaning

Ingredients came in the form of a list of individual ingredients.  For each recipe, lists were converted into a string, all punctuation and numeric digits were removed, and words were lemmatized. 

# EDA

For the training dataset, there were 39,774 rows of recipes, and 20 different regions to predict.  Exploring the data revealed that the classes were fairly imbalanced, and that the most popular ingredients for any particular cuisine are fairly similar across regions.  These observations pose challenges for succuessful modeling. 

# Modeling

Two models were built to predict cuisine region.  The first was a Random Forest.  TFID was used to vectorize the text in a pipeline with the Random Forest model.  Several hyperparameters for the TFIDF vectorizer and Random Forest model were tuned using a Randomized Search CV.  The best parameters revealed that ngrams were not helpful in modeling and stop word removal was unnecessary.  The Random Forest model was overfit despite parameter optimization and yielded a test accuracy of only 75%.

The second model was a Support Vector classifier.  Optimal parameters for the TFIDF vectorizer were carried over from the Random Forrest model, and 10 different values for l2 regulariztion were attempted.  Ultimately, the best performing model used the regularization parameter of C=3 and while also being overfit returned a model accuracy of 80%. 

# Conclusions

While both models improved classification well beyond the baseline model, Support Vector Classification produced superior results to Random Forest.  Given more time, further hyperparameter tuning of SVC and the TFIDF vectorizer could potentially produce better results.  However, this study did not attempt to remedy the clearly imbalanced  classes prior to modeling.  Future studies should attempt to balance classes to improve model performance. 
