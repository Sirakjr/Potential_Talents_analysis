# Potential Talents Analysis

A machine learning-powered talent sourcing and ranking system designed to identify and rank potential candidates for human resources roles. This project implements various NLP techniques to automate the candidate screening process and improve talent acquisition efficiency.

## Project Overview

As a talent sourcing and management company, we face several challenges in finding talented individuals:
1. **Role Understanding**: Need to understand client requirements and ideal candidate profiles
2. **Candidate Assessment**: Identifying what makes a candidate suitable for specific roles
3. **Sourcing Efficiency**: Finding talented individuals in a time-effective manner

This project addresses these challenges by building an automated pipeline that can:
- Rank candidates based on their fitness for specific roles
- Re-rank candidates based on manual feedback (starring mechanism)
- Compare different NLP methods for optimal results

## Features

- **Multiple NLP Methods**: Bag of Words, TF-IDF, BERT, and Sentence Transformers
- **Intelligent Ranking**: Rank candidates based on similarity to target role descriptions
- **Re-ranking System**: Improve rankings based on manually starred candidates
- **Comprehensive Analysis**: Compare different embedding methods for optimal performance
- **Jupyter Notebook Interface**: Interactive analysis and experimentation

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Sirakjr/Potential_Talents_analysis.git
cd Potential_Talents_analysis
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Download required NLTK data (will be done automatically on first run):
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
```

## Data Structure

The dataset contains candidate information with the following attributes:
- `id`: Unique identifier for each candidate (numeric)
- `job_title`: Job title or description for the candidate (text)
- `location`: Geographical location of the candidate (text)
- `connections`: Number of connections the candidate has (text, "500+" means over 500)

## Usage

### Running the Analysis

1. Open the Jupyter notebook:
```bash
jupyter notebook notebooks/Potential_Talents.ipynb
```

2. The notebook contains:
   - Data preprocessing and text cleaning
   - Multiple embedding methods implementation
   - Candidate ranking algorithms
   - Re-ranking functionality based on starred candidates
   - Performance comparison between different methods

### Key Functions

The project implements several key functions:

1. **Text Preprocessing**: 
   - Converts text to lowercase
   - Removes punctuation and extra whitespace
   - Tokenizes and lemmatizes text
   - Removes stopwords

2. **Embedding Methods**:
   - **Bag of Words**: Simple word frequency approach
   - **TF-IDF**: Term frequency-inverse document frequency
   - **BERT**: Contextual embeddings using BERT
   - **Sentence Transformers**: Advanced sentence embeddings

3. **Ranking System**:
   - Calculates similarity scores between candidates and target roles
   - Ranks candidates based on fitness scores
   - Supports re-ranking with starred candidates

## Target Keywords

The system is currently optimized for human resources roles with keywords:
- "Aspiring human resources"
- "Seeking human resources"

## Success Metrics

- **Primary Goal**: Rank candidates based on fitness scores (0-1 probability)
- **Secondary Goal**: Re-rank candidates when specific candidates are starred
- **Performance**: Compare different NLP methods for optimal results

## Project Structure

```
Potential_Talents_analysis/
├── data/
│   └── potential_talents_data.csv    # Candidate dataset
├── notebooks/
│   └── Potential_Talents.ipynb       # Main analysis notebook
├── requirements.txt                  # Python dependencies
└── README.md                        # Project documentation
```

## Dependencies

The project uses the following key libraries:
- **pandas**: Data manipulation and analysis
- **numpy**: Numerical computing
- **scikit-learn**: Machine learning algorithms
- **nltk**: Natural language processing
- **transformers**: BERT and other transformer models
- **torch**: PyTorch for deep learning
- **sentence-transformers**: Advanced sentence embeddings
- **matplotlib/seaborn**: Data visualization

## Performance Notes

- **BERT/Sentence Transformers**: Most accurate but computationally intensive
- **TF-IDF**: Good balance of speed and accuracy
- **Bag of Words**: Fastest but least sophisticated
- **Re-ranking**: Improves results based on manual feedback

## Future Enhancements

- Support for additional role types beyond human resources
- Integration with external talent platforms
- Real-time candidate scoring
- Advanced visualization dashboards
- API endpoints for integration with existing systems

## Contributing

This project is designed for talent sourcing and management companies looking to automate their candidate screening process. Contributions and improvements are welcome!

## License

This project is part of the Apziva curriculum and is designed for educational and practical talent sourcing applications. 