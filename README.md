# Simple Talent Ranking System

A simplified talent ranking system that implements different word embedding methods to rank candidates based on their similarity to a target role description.

## Features

- **5 Different NLP Methods**: Bag of Words, TF-IDF, Word2Vec, FastText, and BERT
- **Automatic Method Comparison**: Compare all methods to find the best one for your data
- **Re-ranking with Starred Candidates**: Improve rankings based on manually selected candidates
- **Simple API**: Easy-to-use functions for ranking candidates

## Installation

1. Install the required dependencies:
```bash
pip install -r requirements.txt
```

2. Make sure you have the data file in the `data/` folder.

## Quick Start

### Basic Usage

```python
from simple_talent_ranking import SimpleTalentRanker

# Initialize the ranker
ranker = SimpleTalentRanker("data/potential-talents - Aspiring human resources - seeking human resources.csv")

# Rank candidates using TF-IDF
ranking = ranker.rank_candidates("aspiring human resources", method='tfidf')

# Show top 10 results
print(ranking.head(10)[['rank', 'id', 'job_title', 'similarity_score']])
```

### Compare All Methods

```python
# Compare all embedding methods
results = ranker.compare_methods("aspiring human resources")

# Find the best method
best_method = ranker.get_best_method("aspiring human resources")
print(f"Best method: {best_method}")
```

### Re-ranking with Starred Candidates

```python
# Star some candidates (IDs: 7, 26, 68)
starred_candidates = [7, 26, 68]

# Re-rank with starred candidates
reranked = ranker.rank_candidates(
    "aspiring human resources", 
    method='tfidf', 
    starred_candidates=starred_candidates
)
```

## Available Methods

1. **Bag of Words (bow)**: Simple word frequency approach
2. **TF-IDF (tfidf)**: Term frequency-inverse document frequency
3. **Word2Vec (word2vec)**: Word embeddings using Word2Vec
4. **FastText (fasttext)**: Subword embeddings using FastText
5. **BERT (bert)**: Contextual embeddings using BERT

## Custom Function

You can create a custom function for easy reuse:

```python
def rank_talents(data_path, target_string, method='tfidf', starred_candidates=None):
    """
    Custom function to rank talents
    
    Args:
        data_path (str): Path to the CSV file
        target_string (str): Target string to compare against
        method (str): Embedding method ('bow', 'tfidf', 'word2vec', 'fasttext', 'bert')
        starred_candidates (list): List of starred candidate IDs for re-ranking
        
    Returns:
        pd.DataFrame: Ranked candidates
    """
    ranker = SimpleTalentRanker(data_path)
    return ranker.rank_candidates(target_string, method, starred_candidates)

# Usage
ranking = rank_talents(
    data_path="data/your_data.csv",
    target_string="software engineer",
    method='bert',
    starred_candidates=[1, 5, 10]
)
```

## Running the Examples

1. **Main demo**: Run the main system with all features
```bash
python simple_talent_ranking.py
```

2. **Usage examples**: Run the usage examples
```bash
python usage_example.py
```

## Output Format

The system returns a pandas DataFrame with the following columns:
- `id`: Candidate ID
- `job_title`: Original job title
- `location`: Candidate location
- `connection`: Number of connections
- `similarity_score`: Normalized similarity score (0-1)
- `rank`: Ranking position

## How Re-ranking Works

When you provide starred candidates, the system:

1. Calculates the average similarity score of starred candidates
2. Boosts scores for candidates similar to the starred ones
3. Re-ranks the entire list based on the adjusted scores

This helps the system learn from your manual selections and improve future rankings.

## Data Requirements

Your CSV file should have these columns:
- `id`: Unique identifier for each candidate
- `job_title`: Job title or description
- `location`: Geographic location
- `connection`: Number of connections (optional)

## Performance Notes

- **BERT**: Most accurate but slowest
- **TF-IDF**: Good balance of speed and accuracy
- **Word2Vec/FastText**: Fast and good for semantic similarity
- **Bag of Words**: Fastest but least sophisticated

## Troubleshooting

1. **Memory issues with BERT**: BERT requires significant memory. If you encounter issues, try using a smaller model or fewer candidates.

2. **Slow performance**: Start with TF-IDF or Word2Vec for faster results.

3. **NLTK data not found**: The system will automatically download required NLTK data on first run.

## Example Results

```
Comparing all methods for target: 'aspiring human resources'
============================================================

Testing BOW...
Top 5 candidates using BOW:
   1. ID   3 - Aspiring Human Resources Professional (Score: 0.8500)
   2. ID   6 - Aspiring Human Resources Specialist (Score: 0.8000)
   3. ID  25 - Student at Humber College and Aspiring Human Resources Generalist (Score: 0.7500)
   4. ID  37 - Student at Humber College and Aspiring Human Resources Generalist (Score: 0.7500)
   5. ID  50 - Student at Humber College and Aspiring Human Resources Generalist (Score: 0.7500)

Testing TF-IDF...
Top 5 candidates using TF-IDF:
   1. ID   3 - Aspiring Human Resources Professional (Score: 0.9200)
   2. ID   6 - Aspiring Human Resources Specialist (Score: 0.8800)
   3. ID  25 - Student at Humber College and Aspiring Human Resources Generalist (Score: 0.8500)
   4. ID  37 - Student at Humber College and Aspiring Human Resources Generalist (Score: 0.8500)
   5. ID  50 - Student at Humber College and Aspiring Human Resources Generalist (Score: 0.8500)
```

This system provides a simple yet powerful way to rank talent candidates using different NLP techniques and learn from your feedback through the starring mechanism. 