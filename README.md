# CAR-Information-Retrieval-Project

In this README you will be guided through our project code and the several steps necessary to generate the needed files and results. 

## Content
* Notebooks and their content
* Pipeline:
  1. Deserialize Files
  2. Data Cleansing
  3. Merge Files
  4. Create Training Files
  5. Creating Representations
  6. Model Training

## Notebooks and their Content
* Notebooks-Linda
  * Create Files: Deserialize the data from fold-0 and merge them with the section title and save them as individual csvs. 
  * Pre-Processing-corpus: Cleans the corpus from stopwords, remove punctuations, lower cases the text, stems them etc.
  * Merging of corpusses with title file: Merge the section title combinations with the cleansed text by using the paragraph IDs.
  * Create Trainingfiles: Creates training files with x articles from individual article.
  * Model Training: All learnt models for Unigram and Word embeddings representation. Contains all evaluation metrics and functions to  generate text representations.

* Notebooks-Celina
  * Exploration
    - concatenation-downsample: Concatenating different representations for downsampled data.
    - concatenation-upsample: Concatenating different representations for upsampled data.
    - determining-dimensions: Exploration on which dimensions might be best using plots.
    - topic-distribution: Exploration of topics using article titles. 
  * Gradient Boosting
    - gradient-boosting-downsample: Gradient Boosting Machines on TF-IDF representation of downsampled data as well as experiments with concatenated data.
    - gradient-boosting-upsample: Gradient Boosting Machines on TF-IDF representation of upsampled data as well as experiments with concatenated data.
  * Multi-Layer Perceptron
    - MLP-downsample: MLP Classifier on TF-IDF representation of downsampled data as well as experiments with concatenated data.
    - MLP-upsample: MLP Classifier on TF-IDF representation of upsampled data as well as experiments with concatenated data.
  * Naive Bayes
    - naive-bayes-downsample: Naive Bayes classifier on TF-IDF representation of downsampled data as well as experiments with concat data.
    - naive-bayes-upsample: Naive Bayes classifier on TF-IDF representation of upsampled data as well as experiments with concat data. 
  * TF-IDF-Generation
    - generate-tfidf-200dim-downsample: TF-IDF generation with 200 dimensions on downsampled data.
    - generate-tfidf-200dim-upsample: TF-IDF generation with 200 dimensions on upsampled data.
    - generate-tfidf-1000dim-downsample: TF-IDF generation with 1000 dimensions on downsampled data.
    - generate-tfidf-1000dim-downsample: TF-IDF generation with 1000 dimensions on upsampled data.
  * Utils
    - utils.py: Module with all necessary functions.
  
## Step 1: Deserialize Files
Make sure that fold-0-base.train.cbor and fold-0-base.train.cbor-toplevel.qrels are placed in the same folder to deserialize the data. 
Also note that the trec-car and cbor tools should be installed.

Notebook "Create Files (Corpuses + Qrels)": 
* Deserialize the data from fold-0 and merge them with the section title and save them as individual csvs. 
* Another possibility is to deserialize the data into one data frame.  

Output Data:
* Corpus25000Articles.csv: 25,000 uncleansed Articles deserialized from fold-0-base.train.cbor 
* Section_titles.csv: all pairwise combinations with the ID, title, Article and Relevance for each paragraph

## Step 2: Data Cleansing
Pre-Processing-corpus: Cleans the corpus from stopwords, remove punctuations, lower cases the text, stems them etc. 
Make sure that Corpus25000.csv is in the same folder.

Output Data:
* CleansedText.csv: Cleansed texts

## Step 3: Merge Files

Notebook "Merging of corpusses with title file": 
* Merge the section title combinations with the cleansed text by using the paragraph IDs.

Make sure that CleansedText.csv and Section_titles.csv are in the same folder.

## Step 4: Create Training Files

Notebook "Create Trainingfiles": 
* Creates training files with x articles from individual article.

Make sure that MergedCorpuses2.csv is in the folder.

Second possibility is to create training files with single files. 
Make sure that MergedCorpuses.csv is in the folder. We used the first function with the single files.

Output Data:
* TrainingSet1000.csv
* TrainingSet2500.csv
* TrainingSet5000.csv

## Step 5: Model Training

Make sure that Scikit Learn and Keras are installed.

Notebook "Model Training": 
* All learnt models for Unigram and Word embeddings representation. 
* Contains all evaluation metrics and functions to generate the text representations. 



