# NLP-Powered Book Discovery & Analysis

A comprehensive natural language processing project for analyzing and exploring book data using modern NLP techniques including semantic search, text classification, and sentiment analysis.

## Project Overview

This project analyzes a dataset of books using various NLP techniques to enable semantic search, classify books by fiction type, and analyze emotional content in book descriptions.

## Features

### 1. Data Exploration
Initial exploratory data analysis of the book dataset to understand the distribution, characteristics, and patterns in the data.

### 2. Vector Search
- **Implementation**: FAISS-based semantic search system
- **Model**: `sentence-transformers/all-mpnet-base-v2`
- **Functionality**: Find similar books based on description similarity to a given prompt
- **Use Case**: Enables semantic book recommendations and similarity searches beyond keyword matching

### 3. Text Classification
- **Task**: Binary classification between Fiction and Non-Fiction categories
- **Model**: `facebook/bart-large-mnli` (zero-shot classification)
- **Accuracy**: 0.778
- **Rationale**: Books were grouped into Fiction and Non-Fiction categories to address class imbalance. Since there are many books in fiction-related categories but individual specific categories (drama, science, etc.) have limited samples, they were consolidated into Non-Fiction to balance the dataset.

### 4. Sentiment Analysis
- **Model**: `j-hartmann/emotion-english-distilroberta-base`
- **Task**: Multi-label emotion detection in book descriptions
- **Emotions Detected**: 
  - Joy
  - Neutral
  - Anger
  - Surprise
  - Disgust
  - Sadness
  - Fear

#### Methodology
The sentiment analysis processes each book description by:
1. Splitting the description into individual sentences
2. Classifying each sentence for all emotion categories
3. Computing the maximum score for each emotion across all sentences
4. Storing the results indexed by ISBN13

This approach captures the peak emotional intensity for each emotion type present in the book's description, providing a nuanced emotional profile of the content.

## Dataset
https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata
## Requirements

```
transformers
sentence-transformers
faiss
numpy
pandas
tqdm
torch
```
