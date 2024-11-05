Certainly! Here is a README file explaining your code:

---

# N-gram Language Model Prediction

This project builds and demonstrates a basic N-gram language model using NLTK (Natural Language Toolkit) with the text data from the book "Emma" by Jane Austen, provided by the NLTK Gutenberg corpus. The code includes Unigram, Bigram, and Trigram models and generates predictions based on sample word sequences.

## Requirements
To run this code, you need to have Python installed along with the following libraries:
- `nltk`
- `pandas` (for handling tabular data, though it's not essential in the given code)

### Installation
To install the necessary packages, run:
```bash
pip install nltk pandas
```

## Code Description

### 1. Loading and Preprocessing the Data
The code first loads sentences from the book *Emma* by Jane Austen, provided by NLTK's Gutenberg corpus. It preprocesses the data by converting all words to lowercase and removing non-alphabetic characters.

```python
from nltk.corpus import gutenberg
corpus = gutenberg.sents("austen-emma.txt")[:1000]
flat_corpus = [word.lower() for sentence in corpus for word in sentence if word.isalpha()]
```

### 2. Building N-gram Models
The code constructs three models based on different N-grams:
- **Unigram Model:** Counts occurrences of individual words.
- **Bigram Model:** Counts occurrences of two consecutive words.
- **Trigram Model:** Counts occurrences of three consecutive words.

```python
from nltk import bigrams, trigrams
from collections import Counter

unigram_counts = Counter(flat_corpus)
bigram_counts = Counter(bigrams(flat_corpus))
trigram_counts = Counter(trigrams(flat_corpus))
```

### 3. Prediction Functions
The code defines functions to make predictions based on each N-gram model:

- **Unigram Prediction:** Randomly selects a word based on unigram probabilities.
- **Bigram Prediction:** Given a word, predicts the next word based on bigram probabilities. If no suitable bigram is found, it falls back to the unigram model.
- **Trigram Prediction:** Given two words, predicts the next word based on trigram probabilities. If no suitable trigram is found, it falls back to the bigram model.

```python
def predict_unigram():
    # Returns a random word based on unigram counts
    ...

def predict_bigram(sequence):
    # Returns the next word based on bigram counts, given the last word in `sequence`
    ...

def predict_trigram(sequence):
    # Returns the next word based on trigram counts, given the last two words in `sequence`
    ...
```

### 4. Predicting for Sample Sequences
A list of sample word sequences is provided, and predictions are made for each sequence using Unigram, Bigram, and Trigram models. The results are stored in a list for easy display.

```python
sample_sequences = [
    ["the"], ["data"], ["machine", "learning"], ["artificial", "intelligence"],
    ["deep", "learning"], ["in", "the"], ["language", "model"], ["the", "future", "of"],
    ["predictive"], ["modeling", "and"]
]

results = []
for sequence in sample_sequences:
    ...
```

### 5. Displaying Results in Table Format
Finally, the results are printed in a table format, showing the original sequence and predictions from each model (Unigram, Bigram, and Trigram).

```python
print(f"{'Sequence of Words':<25} {'Unigram Prediction':<20} {'Bigram Prediction':<20} {'Trigram Prediction':<20}")
for seq, uni, bi, tri in results:
    ...
```

## Sample Output
The sample output shows predictions for each word sequence based on the N-gram models. When Trigram predictions are not available (due to insufficient input length), a placeholder message is shown.

```
Sequence of Words         Unigram Prediction   Bigram Prediction    Trigram Prediction  
the                       mr                   young                N/A (requires 2 words)
data                      his                  never                N/A (requires 2 words)
machine learning          a                    a                    the                 
artificial intelligence   height               small                it                  
...
```

---

