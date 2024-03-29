# Bird's Eye View

## Machine Learning 

- ML is not about algorithms, its a comprehensive approach to solving problems.
- Individual algos are only one piece of the puzzle.
- ML is the practice of teaching computers how to learn patterns from data, often for making decisions or predictions.
- True ML, the computer must be able to learn patterns that it's not explicitly programmed to identify.


## Key Terminology

- Model - a set of patterns learned from data.
- Algorithm - a specific ML process used to train a model.
- Training data - the dataset from which the algorithm learns the model.
- Test data - a new dataset for reliably evaluting model performance.
- Features - Variables (columns) in the dataeslt used to train the model.
- Target variable - a specific variagble you're trying to predict.
- Observations- Data points (rows) in the dataset.

## Machine Learning Tasks

- a task is a specific objective for your algorithms.
- Algos can be swapped in and out, as long as you pick the right task.
- Always try multiple algos because you most likely won't know which one will perform best for your dataset.

## Supervised Learning

- includes tasks fro "labeled" data (you have a target variable).
- used as a advanced form of predictive modeling.
- each observation must be labeled with a "correct answer".
- only then can you build a predictive model because you must tell the algo what's "correct" while training it (hence, "supervising" it).
- Regression is the task for modeling continuous target variables.
- Classfication is the task for modeling categorical (aka "class) target variables.

## Unsupervised Learning

- includes tasks for "unlabeled" data (no target variable).
- often used as a form of automated data analysis or automated signal extraction.
- data has no predetermined "correct answer"
- allow the algorithem to directly learn patterns from the data (without "supervision").
- Clustering is the most common unsupervised learning task. Used for finding groups within your data.

## 3 Elements of Great Machine Learning

1. Human guidance plays a huge role.
2. the quality of your data
3. Do not overfit. An overfit model has "memorized" the noise in the training set, instead of learning the true uderlying patterns.