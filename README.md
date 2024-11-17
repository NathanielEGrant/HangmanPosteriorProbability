# Predictive Word Guessing Model

## Project Overview

This project implements a predictive word guessing model that calculates the probability of guessing the correct letter in a word based on prior word frequencies and specific letter position evidence. The model uses a variety of functions to analyze and predict letters that are most likely to be part of a word, given partial evidence.

## Table of Contents
- [Description](#description)
- [Setup Instructions](#setup-instructions)

## Description

This project is designed to calculate the probability of a correct guess in a word guessing game based on the frequency of words in a dataset. It incorporates the following core steps:
1. **Word Count Analysis:** Counts the occurrences of each word in a text file.
2. **Word Probability Calculation:** Calculates the probability of each word and letter occurring in a word based on observed frequencies.
3. **Predictive Modeling:** Uses the calculated probabilities to predict the best next guess for a word, given partial evidence of correctly and incorrectly guessed letters.

### Key Functions

#### 1. `getWordCount(file_path)`
This function reads a file containing words and their associated counts (separated by a space on each line). It returns a dictionary with the word counts.

#### 2. `getTotalWords(wordCounts)`
Returns the total word count (not unique) from the word count dictionary.

#### 3. `priorProbs(wordCounts, totalCount)`
Calculates the prior probability for each word as a fraction of its count over the total word count.

#### 4. `wordAmounts(priorProbas)`
Prints the top 15 most and least common words based on their probabilities.

#### 5. `predictiveProb(letter, evidence, wordCounts, totalCount)`
Calculates the probability of a letter being part of a word, given prior knowledge about the word's frequencies and evidence of guessed letters.

#### 6. `findBestNextGuess(unguessed_letters, evidence, wordCounts, totalCount)`
Identifies the best next letter to guess based on the highest predictive probability.

## Setup Instructions

### Prerequisites

Before you start, you need to install Python and the required libraries:

1. Install Python 3 (version 3.6+ is recommended).
2. Install the following dependencies using `pip`:

```bash
pip install pandas numpy
```
## Functionality
**Example Code**  
Here is an example of how to use the functions in this project. This code demonstrates how to calculate word counts, compute word probabilities, and predict the next best letter guess.
```python
# Load word counts from a file
file_path = "word_counts_05-1.txt"
wordCounts = getWordCount(file_path)

# Get the total word count
totalCount = getTotalWords(wordCounts)

# Calculate prior probabilities for each word
priorProbas = priorProbs(wordCounts, totalCount)

# Display the most and least common words
wordAmounts(priorProbas)
```
**Predicting the Best Next Guess**  
Given some partial evidence (correct and incorrect guesses), this code will predict the best next letter to guess.

```python
evidence = {
    "correct": {0:'A', 4:'S'},
    "incorrect": ['I']
}

# Generate a list of unguessed letters
unguessedLetters = [chr(i) for i in range(65, 91) if chr(i) not in list(evidence["correct"].values()) + evidence["incorrect"]]

# Get the best next guess
bestLetter, bestProb = findBestNextGuess(unguessedLetters, evidence, wordCounts, totalCount)

print(f"Best next guess: {bestLetter} with probability {bestProb}")
```
## Limitations
The model assumes that all words in the dataset are of equal importance, and it does not account for context or other factors that might influence letter probabilities in natural language.
The predictions are only as accurate as the dataset provided. If the dataset contains errors or inconsistencies, the predictions may be inaccurate.
Embedding the Jupyter Notebook
If you'd like to see the full Jupyter Notebook with code execution and outputs, you can view it here.

## Conclusion
This predictive word guessing model uses word frequency data and probabilistic modeling to make educated guesses about the next letter in a word, based on prior knowledge of word and letter occurrences. The methods employed in this project can be applied to more complex natural language processing tasks, such as predictive text input or game-based word guessing.
