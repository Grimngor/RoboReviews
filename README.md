# RoboReviews

RoboReviews is an AI-driven project aimed at analyzing customer reviews to provide valuable insights that help improve products and services. This project is a part of my AI Engineering BootCamp at Ironhack. The goal is to utilize various machine learning techniques to understand customer feedback better and make informed blog-style productrecommendations.
This README outlines the installation steps, usage instructions, and key concepts.

## Table of Contents
- [Key Features](#key-features)
- [Data Preparation](#data-preparation)
- [Architecture](#architecture)
- [Current Status](#current-status)
- [Executing the Code](#executing-the-code)
- [Technologies Used](#technologies-used)

---

## Key Features

The project focuses on three primary tasks:

1. **Sentiment Analysis**: Classify customer reviews into positive, negative, or neutral categories.
2. **Product Category Clustering**: Cluster products into meaningful categories for better market understanding.
3. **Review Summarization**: Use generative AI to summarize reviews, recommending the top products for each identified category.

## Data Preparation

Data preparation is crucial for the success of the project, and several steps were taken to ensure quality:

1. **Loading and Cleaning**: Data from multiple CSV files were loaded in parallel, cleaned, and preprocessed by selecting relevant columns and removing unnecessary rows.
2. **Filtering Short Reviews**: Reviews with insufficient content were filtered out to focus on meaningful feedback.
3. **Deduplication and Sampling**: Duplicate reviews and null values were removed, and balanced sampling was performed to ensure equal representation of sentiment groups.

## Architecture

- **Sentiment Analysis**: A fine-tuned DistilRoBERTa model is used to classify the sentiment of customer reviews as positive, neutral, or negative. Initially, VADER was explored, but due to its limitations in capturing nuanced sentiments, the decision was made to switch to DistilRoBERTa for improved performance.

- **Product Clustering**: Product reviews are clustered into 4-6 categories using paraphrase-MiniLM-L6-v2. This model was chosen for its efficiency and optimization for sentence embeddings, which made it suitable for clustering tasks.

- **Generative AI for Review Summarization**: This task aims to generate a summary of reviews to recommend top products for each category. This part of the project is in the initial stages of development.

## Current Status

- **Sentiment Analysis Model**: Functional, but needs further optimization.
- **Clustering Model**: Built, but requires improvements to achieve better grouping results.
- **Generative Model**: In the early stages, with initial ideas being implemented.

## Executing the Code

1. Running ```"0_Data_Preprocessing.ipynb"``` will generate ```"final_dataset.csv"```. But it needs 4 pre-processed input dataframes that I wasn't able to upload somewhere. So instead I'm including a reduced (70k instead of 200k rows) version of ```final_dataset.csv``` in order to be able to execute the next file.
2. Running ```1_Sentiment_Dev.ipynb``` will start by reading ```"final_dataset.csv"``` which will generate sentiment labels and add them to  ```"final_dataset_sent.pkl"``` for the next model to use; And a folder, ```sentiment-fine-tuned-distilroberta``` with the model after training it.
3. ```2_Clustering_Dev.ipynb``` and ```3_Summarizing_Dev``` are not finished and I didn't have time to ensure they run. but the clustering code was supposed to generate ```final_dataset_clust.pkl``` with the groups added for the generative model to use.

## Technologies Used

- **Python** for data processing and modeling
- **HuggingFace Transformers** for fine-tuning pre-trained models
- **Scikit-Learn** for clustering analysis
- **Pandas and Polars** for data manipulation
