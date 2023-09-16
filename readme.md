# Autocorrect Feature Using NLP with Python

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Natural Language Processing (NLP)](#natural-language-processing-nlp)
- [Autocorrect Feature](#autocorrect-feature)
- [Building Autocorrect Feature](#building-autocorrect-feature)
  - [Installing Libraries](#installing-libraries)
  - [Reading Text File (Dictionary)](#reading-text-file-dictionary)
  - [Frequency and Probability of Dictionary Words](#frequency-and-probability-of-dictionary-words)
  - [Implementing Edit Word Functions](#implementing-edit-word-functions)
- [Conclusion](#conclusion)

## Introduction

One of the features that utilize Natural Language Processing (NLP) is the Autocorrect function. This feature is commonly found on smartphone keyboards and is programmed to correct spelling errors and suggest the most similar words when a word is not found in the dictionary. In this guide, we'll explore NLP and use Python to build an autocorrect feature.

## Prerequisites

To follow along with this tutorial, you should:

- Have a basic understanding of Natural Language Processing (NLP) and Machine Learning concepts.
- Be familiar with Python and the Python libraries commonly used for NLP.
- Use an integrated development environment (IDE) like PyCharm or any other Python IDE.

## Natural Language Processing (NLP)

Natural Language Processing (NLP) is a branch of Artificial Intelligence that enables computers to understand and process natural human language. NLP has a wide range of applications, including:

- Search autocorrect and autocomplete.
- Language translation and grammar checkers.
- Chatbots and social media monitoring.
- Email filtering and voice assistants.

In this tutorial, we will focus on how NLP is used in autocorrection systems.

## Autocorrect Feature

The Autocorrect feature is designed to correct spelling errors and suggest similar words while typing. It relies on NLP to compare typed words with those in its vocabulary dictionary. Here are the key steps involved in building an autocorrect feature:

1. Identifying misspelled words.
2. Finding words that are a certain edit distance away from the misspelled word (insert, delete, swap, replace).
3. Filtering suggested candidates to include only correctly spelled words.
4. Ordering filtered candidates based on word probabilities.
5. Choosing the most likely candidate based on probabilities.

## Building Autocorrect Feature

To build an autocorrect system, we'll start by using a vocabulary dictionary from a text file. Let's go through the steps.

### Installing Libraries

To begin, install the required Python libraries using the following commands:

```bash
pip install pattern
pip install pyspellchecker
pip install autocorrect
pip install textblob
pip install textdistance
```
### Reading Text File (Dictionary)
We need a vocabulary dictionary to develop our autocorrect system. In this tutorial, we'll use a sample.txt file containing the 1000 most commonly used words.

python

```bash
# Step 1: Data Preprocessing
import re
from collections import Counter
import numpy as np
import pandas as pd

w = []  # Words
with open('sample.txt', 'r', encoding="utf8") as f:
    file_name_data = f.read()
    file_name_data = file_name_data.lower()
    w = re.findall('\w+', file_name_data)

v = set(w)  # Vocabulary
print(f"The first 10 words in our dictionary are: \n{w[0:10]}")
print(f"The dictionary has {len(v)} words.")
```
### Frequency and Probability of Dictionary Words
Now, let's find the frequency of words in our dictionary and calculate their probabilities.

```bash
# A function to get word frequencies
def get_count(words):
    word_count_dict = {}
    for word in words:
        if word in word_count_dict:
            word_count_dict[word] += 1
        else:
            word_count_dict[word] = 1
    return word_count_dict

word_count_dict = get_count(w)
print(f"There are {len(word_count_dict)} key-value pairs.")
```
```bash
# A function to calculate word probabilities
def get_probs(word_count_dict):
    probs = {}
    m = sum(word_count_dict.values())
    for key in word_count_dict.keys():
        probs[key] = word_count_dict[key] / m
    return probs
```
### Implementing Edit Word Functions
We need to implement edit functions for delete, switch, replace, and insert operations.

```bash
# Function to delete a letter from a word
def DeleteLetter(word):
    # Implementation...

# Function to swap two adjacent letters in a word
def SwitchLetter(word):
    # Implementation...

# Function to replace one letter with another in a word
def replace_letter(word):
    # Implementation...

# Function to insert an additional character into a word
def insert_letter(word):
    # Implementation...
```
We also combine these edit functions to perform autocorrect operations:

```bash
# Function to perform one edit operation on a word
def edit_one_letter(word, allow_switches=True):
    # Implementation...

# Function to perform two edit operations on a word
def edit_two_letters(word, allow_switches=True):
    # Implementation...

# Function to get corrected word suggestions
def get_corrections(word, probs, vocab, n=2):
    # Implementation...
```
In the end, the autocorrect system will prompt the user to input a word and provide suggestions based on the dictionary and probabilities.

## Conclusion
In this tutorial, we have explored how Natural Language Processing (NLP) is used to build an autocorrect feature in Python. NLP enables computers to understand and process human language, making autocorrection systems more efficient and user-friendly.


Happy coding!
