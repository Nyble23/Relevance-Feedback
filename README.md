# Relevance-Feedback #

We will be working on[20newsgroup dataset](https://archive.ics.uci.edu/ml/datasets/Twenty+Newsgroups)
This dataset consists of 20 folders containing 19,997 files in total.

**Rocchio Algorithm** was the relevance feedback mechanism introduced in and populrized by Salton's SMART system around 1970.
In the real IR query context, we have a user query and partial knowledge of known relevant and non-relevant documents.
The algorithm generates a modified query vector based on the relevance feedback provided by the user, and thus results in fetching relevant results.
Thus, relevance feedback can improve both recall and precision.

## Pre-processing Steps ##
* All the special characters including punctuation symbols from the given data are removed.
* Numbers are converted to words using num2words library.
* Stop words present in the NLTK corpus.
* Meta -data present as header and footer in the data files is removed.
* The tokens generated are lemmatised using NLTK wordnet lemmatiser.

#### Assumptions ####
* Contractions are not handled separately. Eg: We’ll is converted to “Well” after
pre-processing step.
* Query will not be mis-spelled.

## Working ##
1. Building mapping dictionary:
* For each of the file a mapping dictionary is created, which assigns docID to each file.
* Key for this dictionary is of the form “directory/filename” and value is a number that
corresponds to it’s docID.
2. Building inverted index:
* A dictionary is built in which every token is key and a list of docIDs is its value.
3. Building tf-idf dictionary/ new_index:
* Using the tf and idf values already computed, a new inverted index is built. In this, the
key is term, and the value is another dictionary which contains docIDs along with the
corresponding tf-idf weights.
* This new index is used for the computation in Rocchio’s Algorithm.
4. User is asked to enter the number of relevance feedbacks and the number of top results
desired by the user.
5. The Rocchio algorithm is run on each of the queries given in the question and the outputs are
generated based on user relevance feedback.
6. For each of the iteration, **PR(Precision-Recall) curve** and **TNSE graph** is plotted.
7. The **MAP(Mean Average Precision) value** for each iteration is reported.
