# Classifying TikTok Videos Using Machine Learning

## Project Overview

### Context
TikTok users can report videos that they believe violate the platform's terms of service. Due to the immense volume of videos created and viewed daily, many reported videos cannot be individually reviewed by a human moderator. Analysis shows that authors violating terms of service are more likely to present claims rather than opinions. Therefore, distinguishing between claim-presenting and opinion-presenting videos is crucial.

### Goal
Build a model to predict whether a TikTok video presents a "claim" or an "opinion." A successful prediction model will help TikTok reduce the backlog of user reports and prioritize them more efficiently. Videos labeled as opinions will be less likely to go to human review, while those labeled as claims will undergo further scrutiny to determine if they should be prioritized for review.

## Project Structure

1. [Exploratory Data Analysis](#exploratory-data-analysis)
2. [Feature Engineering](#feature-engineering)
3. [Data Splitting](#data-splitting)
4. [Text Tokenization](#text-tokenization)
5. [Modeling](#modeling)
6. [Conclusion](#conclusion)

## Exploratory Data Analysis

Conduct an in-depth exploratory analysis to understand the dataset's structure, distribution, and key characteristics.

## Feature Engineering

Perform feature selection, extraction, and transformation to prepare the data for modeling.

## Data Splitting

- Split the data into training and testing sets (80/20).
- Further split the training set into training and validation sets (75/25), resulting in a final 60/20/20 train/validate/test split.

## Text Tokenization

- Extract numerical features from the `video_transcription_text`.
- Use `CountVectorizer` to break each video's transcription text into both 2-grams and 3-grams.
- Select the 15 most frequently occurring tokens from the entire dataset as features.

## Modeling

### Task
Binary Classification - Predict whether a video is a claim or opinion.

### Models Compared
- Random Forest
- XGBoost

#### Modeling Workflow and Selection
- Given ~20,000 videos in the sample, prioritize minimizing false negatives to ensure potentially harmful content is reviewed.
- Evaluation Metric: **Recall** (due to the higher cost of misclassifying a claim as an opinion).

### Best Model
- Random Forest performed slightly better than XGBoost and was selected for final predictions.

## Conclusion

Both Random Forest and XGBoost models showed excellent performance, with Random Forest slightly outperforming. This model was used to predict the labels on the test data, providing a robust solution to prioritize TikTok video reviews.
