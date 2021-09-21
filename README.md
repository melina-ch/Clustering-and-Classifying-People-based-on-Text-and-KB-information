<h1 align="center">
Clustering and Classifying People based on Text and
KB information
</h2>
<p align="center">

## Overview

This repository contains a jupyter notebook that represents a complete Data Science project written explicitly in [Python 3](https://www.python.org/). We collect information from Wikipedia about people belonging to different categories (Writers, Politicians, Singers, Mathematicians, Architects and Painters), preprocess the text and perform clustering and classification.

## Requirements
* [nltk](https://www.nltk.org/)
* [SPARQLWrapper](https://github.com/RDFLib/sparqlwrapper)
* [Pandas](https://pandas.pydata.org/)
* [sklearn](https://scikit-learn.org/stable/)
* [NumPy](https://numpy.org)
* [Matplotlib](https://matplotlib.org/)
* [requests](https://docs.python-requests.org/en/master/)
* [seaborn](https://seaborn.pydata.org/)
* [spaCy](https://spacy.io/)
* [en_core_web_sml](https://spacy.io/models/en#en_core_web_sm)
* [wikipedia](https://pypi.org/project/wikipedia/)
* [wordcloud](https://github.com/amueller/word_cloud)

## Install requirements
In order to install requirements run ```pip install -r requirements.txt```

## Usage
You can change the values for n , k (number of sentences per page and number of pages per occupation). 

## Corpus extraction

We compile a text corpus from Wikipedia, made of plain text sentences and focused on 6 categories: architects, mathematicians, painters, politicians, singers and writers. Our program takes as input k people per category and n sentences per person.

For each person, we retrieve their corresponding Wikipedia page title, their Wikidata description, the n first sentences of the Wikipedia page content and we store them into a csv file along with their corresponding category and data type (artists (A) or non-artists (Z)).

## Preprocessing 

Various preprocessing methods are used in order to compare results. 

## Clustering

Three types of vectorization have been implemented. Clustering is done with KMeans algorithm.

## Classification

Classification is performed with multiple algorithms and the results are compared. In our case, the model Random Forest classifier gives the best classification results, therefore it is used when visualizing the classification reports, accuracy and matrices.

In case another model gives better results, you are welcome to change the model on this cell:

"category_classification= RFC(df_clean[best_score[0]], df_clean['type']) 
subcategory_classification=RFC(df_clean[best_score[0]], df_clean['occupation'])
category_description_classification=RFC(df_clean[description_preprocessing((best_score[0]))], df_clean['type'])
subategory_description_classification=RFC(df_clean[description_preprocessing((best_score[0]))], df_clean['occupation'])"

You will find that there is a different function for each model. Simply replace "RFC" with the corresponding name.

## Output

Running the code will result in two csv files (original corpus and preprocessed corpus) to be saved in the working directory.
The files are named "result_.csv" and "df_clean_.csv" respectively.

The results for clustering and classification are printed automatically. The best clustering result in terms of homogeneity score is further depicted with word-clouds.
Best classification results are also presented in details (per category and subcategory).
