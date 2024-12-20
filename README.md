# Comprehensive NLP Analysis of Airbnb Reviews for Improved Decision-Making

## Overview
This project aims to transform unstructured Airbnb review data into actionable insights using advanced Natural Language Processing (NLP) techniques. By performing sentiment analysis, aspect-based sentiment classification, and automated summarization, we enable hosts, guests, and stakeholders to quickly derive value from large volumes of textual feedback. The insights gained can inform business improvements, guide travelers’ booking decisions, and enhance user experience on the platform.

## Key Objectives
- **Sentiment Analysis:** Classify Airbnb reviews into positive or negative categories.
- **Aspect-Based Sentiment Analysis (ABSA):** Identify key aspects (e.g., location, cleanliness, host interaction) from the reviews and determine the sentiment polarity for each aspect.
- **Summarization:** Generate concise, coherent summaries of multiple reviews for a given listing, allowing users to grasp the overall sentiment and key themes quickly.

---

## Data Description
- **Input Dataset:** `NYC_2021_airbnb_reviews_data1.csv`
- **Columns:**
  - `listing_id`: Unique identifier for each Airbnb listing.
  - `url`: Link to the Airbnb listing.
  - `review_posted_date`: Date (month, year) when the review was posted.
  - `review`: Textual content of the guest review.

---

## Prerequisites and Setup

### Python Version
- **Recommended:** Python 3.8 or higher  
  Using a recent version ensures compatibility with the latest libraries.

### Environment
- Use a virtual environment (e.g., `venv` or `conda`) to isolate dependencies and avoid conflicts.

### GPU/CPU
- **Recommended:** GPU acceleration for faster model training and inference.  
  Scripts will run on CPU if a GPU is unavailable, though operations may be slower.

### Python Libraries and Dependencies
The following Python libraries are required:
- `pandas`: Data manipulation and CSV handling.
- `numpy`: Numerical computations.
- `nltk`: Tokenization, lemmatization, and POS tagging.
- `langdetect`: Language detection and filtering non-English reviews.
- `contractions`: Expanding contractions in text.
- `emoji`: Handling and converting emojis to text.
- `tqdm`: Progress bars for processing large datasets.
- `transformers`: Pre-trained models (e.g., BERT, T5) for sentiment analysis and summarization.
- `datasets`: Managing datasets compatible with `transformers`.
- `scikit-learn`: Metrics and clustering (e.g., KMeans).
- `gensim`: Training Word2Vec models for aspect extraction.
- `matplotlib`: Creating visualizations and plots.
- `seaborn`: Advanced statistical plots.
- `wordcloud`: Generating word clouds.
- `re`: Regular expressions for text cleaning.

#### Sample Installation Command:
pip install pandas numpy nltk langdetect contractions emoji tqdm transformers datasets scikit-learn gensim matplotlib seaborn wordcloud

# NLTK Data

**Note:** The code uses several NLTK resources to process text. Ensure these resources are downloaded before running the scripts. The following NLTK packages are used:  
- **punkt**: For tokenization.  
- **wordnet**: For lemmatization.  
- **stopwords**: For removing common English stopwords.  
- **averaged_perceptron_tagger**: For POS tagging (to identify nouns for aspect extraction).

# Scripts and Usage

## 1. Sentiment Analysis Pipeline (`Phase1_SentimentalCode.py`)

**Purpose:**  
- Load and preprocess Airbnb reviews.  
- Detect language and filter only English reviews.  
- Expand contractions, clean text, tokenize, and lemmatize.  
- Generate initial sentiment labels using a pre-trained DistilBERT sentiment model.  
- Fine-tune a BERT model for sentiment classification.  
- Save the processed dataset with sentiment labels.

**Run:**  
```bash
python Phase1_SentimentalCode.py

```

## Output
- `processed_reviews_SentimentLabels.csv`
- Console logs showing training and evaluation metrics

---

## 2. Sentiment Visualization (`Sentiment_plots.ipynb`)

### Purpose
- Load the CSV file: `processed_reviews_SentimentLabels.csv`.
- Visualize the distribution of sentiments.
- Create bar charts for sentiment distribution.
- Generate time-series line charts to analyze yearly sentiment trends.
- Create word clouds and bigram frequency charts for positive and negative reviews.

### Run
```bash
jupyter notebook Sentiment_plots.ipynb
```

- Open the notebook in a browser and run the cells to produce the plots.

---

## 3. Aspect-Based Sentiment Analysis (`ABSA_DataProcessing.py`)

### Purpose
- Load the CSV file: `processed_reviews_SentimentLabels.csv`.
- Tokenize and lemmatize reviews for Word2Vec model training.
- Train Word2Vec to produce embeddings for the vocabulary.
- Extract nouns and cluster them using KMeans to identify aspects.
- Map aspects to each review and create an aspect-level sentiment dataset.

### Run
```bash
python ABSA_DataProcessing.py
```

## Output
- `AspectbasedSentimentAnalysis.csv` with columns: `listing_id`, `review_posted_date`, `cleaned_review`, `aspects`, and `sentiment_label`.

---

## 4. Aspect-Based Visualization (`ABSA_plots.ipynb`)

### Purpose
- Load `AspectbasedSentimentAnalysis.csv`.
- Create visualizations such as:
  - Heatmaps for sentiment per aspect.
  - Radar charts for specific listings.
  - Stacked area charts to show aspect sentiment evolution over time.

### Note
- Open as a notebook (`.ipynb` format) in Jupyter and run cells to produce the visualizations.

---

## 5. Summarization (`FinalSummarization.py`)

### Purpose
- Prompt the user for a `listing_id` (e.g., `10452`).
- Summarize all reviews associated with that listing using a T5 model.
- Provide a concise narrative capturing:
  - Host personality
  - Accommodation quality
  - Neighborhood vibe
  - Safety
  - Transportation options

### Run
```bash
python FinalSummarization.py
```

## Output
- A final summary displayed in the console.

---

## Interpreting the Results

### Sentiment Analysis Results
- High accuracy and F1 scores indicate the model’s strong performance in classifying reviews.
- Positive reviews dominate, suggesting general guest satisfaction.

### Aspect-Based Insights
- Clustering nouns into aspects reveals what specifically guests value (e.g., location, cleanliness) and what they dislike (e.g., cancellations).
- The aspect-level sentiment dataset allows you to identify areas needing attention and improvement.

### Visualizations
- The provided plots (bar charts, heatmaps, line graphs, radar charts, stacked area plots, word clouds) offer a comprehensive view of sentiment trends, key words, aspect distributions, and temporal changes.

### Summarization
- Automatically generated summaries help users quickly understand the essence of thousands of reviews.
- Focuses on critical attributes mentioned frequently by guests.

---

## References
- **Dataset:** [NYC Airbnb Reviews 2021 (Kaggle)](https://www.kaggle.com/datasets)
- **BERT:** Devlin, J. et al. (2019). *BERT: Pre-training of Deep Bidirectional Transformers*.
- **T5:** Raffel, C. et al. (2020). *Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer*.
- **Word2Vec:** Mikolov, T. et al. (2013). *Distributed Representations of Words and Phrases*.
- **Hugging Face Transformers:** [https://huggingface.co/transformers/](https://huggingface.co/transformers/)
- **NLTK:** [https://www.nltk.org/](https://www.nltk.org/)

---

## Contact
For questions or feedback, please open an issue in this repository or contact the project maintainers directly.

