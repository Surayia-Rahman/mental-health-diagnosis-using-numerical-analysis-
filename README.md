 # a. depression diagnosis 

  ## 1. Data Collection
Attempted to load data from Kaggle, but encountered permission errors:

kaggle.json file missing

403 Forbidden when accessing the dataset

Proceeded by using the file 1- mental-illnesses-prevalence.csv already available locally.

 ## 2. Data Cleaning
Loaded the dataset and found it had 6,420 rows and 8 columns.

Identified 270 missing values in the Code column.

Dropped rows with missing values, resulting in 6,150 rows.

## 3. Exploratory Data Analysis (EDA)
Explored unique years (1990–2019).

Checked the distribution of Anxiety Disorders (share of population) using sns.histplot() → Slightly right-skewed distribution.

## 4. Correlation Analysis
Dropped Entity and Code columns to focus on numerical data.

Created a correlation matrix heatmap:

Anxiety disorders correlated moderately with:

- Bipolar disorders (r = 0.57)
- Eating disorders (r = 0.59)

Low correlation with Year, Depression, Schizophrenia.

Based on correlation:

Retained only features with correlation ≥ 0.5 with Anxiety Disorders:

- Bipolar Disorders
- Eating Disorders

## 5. Machine Learning – Linear Regression

Split data into:

X: Bipolar and Eating Disorders (features)

y: Anxiety Disorders (target)

Used 80/20 train-test split.

Trained a Linear Regression model.

Evaluated with Mean Squared Error (MSE):

📉 MSE: 0.6689 → Indicates moderate prediction error.

## Visualizations:

Actual vs. Predicted Scatter Plot: Showed linear trend with some spread.

Residual Histogram: Centered around 0, slightly skewed.

## Model Coefficients:

Bipolar Disorders Coefficient ≈ 1.44

Eating Disorders Coefficient ≈ 2.81

## Interpretation: 
A unit increase in eating disorders share has a higher impact on anxiety disorders than bipolar disorders.

Cross-validated using 5-fold CV (though the scores output was cut off).


# b. likely to suicide 

## Data Preprocessing & Visualization

Separated the dataset into suicide and non-suicide classes.

Generated word clouds to visualize common words in both categories.

Analyzed and compared word counts in each category using distribution plots.

## Text Vectorization

Tokenized and cleaned the text using RegexpTokenizer and removed stopwords.

Used the Google News Word2Vec model to vectorize the text by averaging the vectors of valid tokens.

Created a new column in the dataframe to store these vectors.

Dropped entries with missing vectors to clean the dataset.

## Dataset Preparation for Model

Converted class labels into binary format (1 for suicide, 0 for non-suicide).

Split the data into training and testing sets.

Converted the data into PyTorch tensors and created DataLoaders for efficient batching.

## Model Definition & Training

Defined a deep neural network with 3 hidden layers and ReLU activations, ending with a Sigmoid output layer.

Trained the model using binary cross-entropy loss and the Adam optimizer.

Tracked and visualized the training loss over 50 epochs.


