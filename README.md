# AI Hallucination Checker

A Python tool to measure the semantic similarity between a source text and a generated text, helping to identify potential hallucinations in AI-generated content.

## Overview

This tool uses natural language processing techniques to compare an original source text with AI-generated text, producing a consistency score that indicates how closely the generated text aligns with the information in the source. Lower scores suggest potential hallucinations or factual inconsistencies.

## Features

- Text preprocessing to remove noise (stopwords, punctuation)
- Sentence embeddings using spaCy's vector representation
- Cosine similarity calculation between text embeddings
- Simple API for comparing source and generated texts

## Requirements

- Python 3.6+
- spaCy
- NumPy
- NLTK

## Installation

```bash
# Install required packages
pip install spacy numpy nltk

# Download required models
python -m spacy download en_core_web_md
python -m nltk.downloader punkt
python -m nltk.downloader stopwords
```

## Usage

```python
from hallucination_detector import hallucination_score

# Example texts
source = """
The Renaissance was a period of cultural rebirth in Europe that began in Italy 
during the 14th century. This movement was characterized by renewed interest in 
classical art and learning, leading to significant advances in art, 
architecture, and science.
"""

generated = """
The Renaissance started in Italy in the 1300s and was a time when European 
culture experienced a major revival. People became very interested in studying 
ancient Greek and Roman works, which sparked big developments in things like 
painting, building design, and scientific discovery.
"""

# Calculate hallucination score
score = hallucination_score(source, generated)
print(f"Consistency Score: {score:.4f}")
```

## How It Works

1. **Text Preprocessing**: Converts text to lowercase, removes stopwords and punctuation to focus on meaningful content.
2. **Vector Embeddings**: Uses spaCy's medium English model to create vector representations of the preprocessed texts.
3. **Similarity Calculation**: Computes the cosine similarity between the source and generated text vectors.
4. **Score Interpretation**: Returns a score between 0 and 1, where higher values indicate greater semantic similarity.

## Functions

- `preprocess_text(text)`: Cleans and normalizes input text
- `get_sentence_embeddings(nlp, text)`: Creates vector representation using spaCy
- `calculate_similarity(vec1, vec2)`: Computes cosine similarity between vectors
- `hallucination_score(source_text, generated_text)`: Main function that orchestrates the process

## Limitations

- Relies on semantic similarity rather than factual verification
- May not detect subtle factual errors that preserve overall semantic meaning
- Performance depends on the quality and coverage of the spaCy model used

## Future Improvements

- Support for multiple languages
- Integration with fact-checking databases
- Enhanced detection of numerical inconsistencies
- Sentence-level analysis for more granular hallucination detection

## Author

Mini Course Generator