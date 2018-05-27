# CAR-Information-Retrieval-Project

In this README you will be guided through our project code and the several steps necessary to generate the needed files and results. 

## Content
* Notebooks and their content
* Step 1: Deserialize Files
* Step 2: Data Cleansing
* Step 3: Merge Files
* Step 4: Create Training Files
* Step 5: Creating Representations
* Step 6: Model Training

## Notebooks and their Content
### Notebooks-Linda
  * Create Files: Deserialize the data from fold-0 and merge them with the section title and save them as individual csvs. 
  * Pre-Processing-corpus: Cleans the corpus from stopwords, remove punctuations, lower cases the text, stems them etc.
  * Merging of corpusses with title file: Merge the section title combinations with the cleansed text by using the paragraph IDs.
  * Create Trainingfiles: Creates training files with x articles from individual article.
  * Model Training: All learnt models for Unigram and Word embeddings representation. Contains all evaluation metrics and functions to  generate text representations.

### Notebooks-Celina
  * Exploration
    * concatenation-downsample: Concatenating different representations for downsampled data.
    * concatenation-upsample: Concatenating different representations for upsampled data.
    * determining-dimensions: Exploration on which dimensions might be best using plots.
    * topic-distribution: Exploration of topics using article titles. 
  * Gradient Boosting
    * gradient-boosting-downsample: Gradient Boosting Machines on TF-IDF representation of downsampled data as well as experiments with concatenated data.
    * gradient-boosting-upsample: Gradient Boosting Machines on TF-IDF representation of upsampled data as well as experiments with concatenated data.
  * Multi-Layer Perceptron
    * MLP-downsample: MLP Classifier on TF-IDF representation of downsampled data as well as experiments with concatenated data.
    * MLP-upsample: MLP Classifier on TF-IDF representation of upsampled data as well as experiments with concatenated data.
  * Naive Bayes
    * naive-bayes-downsample: Naive Bayes classifier on TF-IDF representation of downsampled data as well as experiments with concat data.
    * naive-bayes-upsample: Naive Bayes classifier on TF-IDF representation of upsampled data as well as experiments with concat data. 
  * TF-IDF-Generation
    * generate-tfidf-200dim-downsample: TF-IDF generation with 200 dimensions on downsampled data.
    * generate-tfidf-200dim-upsample: TF-IDF generation with 200 dimensions on upsampled data.
    * generate-tfidf-1000dim-downsample: TF-IDF generation with 1000 dimensions on downsampled data.
    * generate-tfidf-1000dim-downsample: TF-IDF generation with 1000 dimensions on upsampled data.
  * Utils
    * utils.py: Module with all necessary functions.

## Step 1: Deserialize Files
Needed Notebooks:
* Notebooks-Linda/Create Files (Corpuses + Qrels)

Output Data:
Output Data:
* Corpus25000Articles.csv: 25,000 uncleansed Articles deserialized from fold-0-base.train.cbor 
* Section_titles.csv: all pairwise combinations with the ID, title, Article and Relevance for each paragraph

Additional Information: 
* Make sure that fold-0-base.train.cbor and fold-0-base.train.cbor-toplevel.qrels are placed in the same folder to deserialize the data. 
* Also note that the trec-car and cbor tools should be installed.

## Step 2: Data Cleansing
Needed Notebooks:
* Notebooks-Linda/Pre-Processing-corpus

Output Data:
* CleansedText.csv: Cleansed texts

## Step 3: Merge Files
Needed Notebooks:
* Notebooks-Linda/Merging of corpusses with title file 

Additional Information: 
* Make sure that CleansedText.csv and Section_titles.csv are in the same folder.

## Step 4: Create Training Files
Needed Notebooks:
* Notebooks-Linda/Create Trainingfiles

Output Data:
* TrainingSet1000.csv
* TrainingSet2500.csv
* TrainingSet5000.csv

Additional Information: 
* Make sure that MergedCorpuses2.csv is in the folder.
* Second possibility is to create training files with single files. 
* Make sure that MergedCorpuses.csv is in the folder. We used the first function with the single files.

## Step 5: Creating Representations

### Step 5.1: Creating Unigrams
Needed Notebook:
* Notebooks-Linda/Model Training

### Step 5.2: Creating Unigrams
Needed Notebook:
* Notebooks-Linda/Model Training

### Step 5.3: Creating TF-IDF
Needed Notebooks:
* Notebooks-Celina/TF-IDF Generation/generate-tfidf-200dim-downsample
* Notebooks-Celina/TF-IDF Generation/generate-tfidf-200dim-upsample
* Notebooks-Celina/TF-IDF Generation/generate-tfidf-1000dim-downsample
* Notebooks-Celina/TF-IDF Generation/generate-tfidf-1000dim-upsample

Output Data:
* Downsampled Version:
  * ../../Sets-Downsampled/TF-IDF/200/train1000_tfidf.csv
  * ../../Sets-Downsampled/TF-IDF/200/train2500_tfidf.csv
  * ../../Sets-Downsampled/TF-IDF/200/train5000_tfidf.csv
  * ../../Sets-Downsampled/TF-IDF/1000/train1000_tfidf.csv
  * ../../Sets-Downsampled/TF-IDF/1000/train2500_tfidf.csv
  * ../../Sets-Downsampled/TF-IDF/1000/train5000_tfidf.csv

* Upsampled Version: 
  * ../../Sets-Upsampled/TF-IDF/200/train1000_tfidf.csv
  * ../../Sets-Upsampled/TF-IDF/200/train2500_tfidf.csv
  * ../../Sets-Upsampled/TF-IDF/200/train5000_tfidf.csv
  * ../../Sets-Upsampled/TF-IDF/1000/train1000_tfidf.csv
  * ../../Sets-Upsampled/TF-IDF/1000/train2500_tfidf.csv
  * ../../Sets-Upsampled/TF-IDF/1000/train5000_tfidf.csv
  
* Validation Sets:
  * ../../Sets-Validation/TF-IDF/200/validate1000_tfidf.csv
  * ../../Sets-Validation/TF-IDF/200/validate2500_tfidf.csv
  * ../../Sets-Validation/TF-IDF/200/validate5000_tfidf.csv

Additional Information: 
* The path for reading the downsampled data is set to: "../../Sets-Downsampled/Basic/Train_x_downsample.csv" where x is a place holder for 1000,2500 or 5000
* The path for the upsampled data is set to: "../../Sets-Upsampled/Basic/Train_x_upsample.csv"
* The path for reading the validation sets is set to "../../Sets-Validation/Basic/Validation_x_cleansed.csv"

## Step 6: Model Training
Needed Notebook:
* Notebooks-Linda/Model Training
* Notebooks-Celina/Gradient Boosting/gradient-boosting-upsample
* Notebooks-Celina/Gradient Boosting/gradient-boosting-downsample
* Notebooks-Celina/Multi-Layer Perceptron/MLP-upsample
* Notebooks-Celina/Multi-Layer Perceptron/MLP-downsample
* Notebooks-Celina/Naive Bayes/naive-bayes-upsample
* Notebooks-Celina/Naive Bayes/naives-bayes-upsample

Additional Information:
* Make sure that Scikit Learn and Keras are installed.
* For all model in Notebooks-Celina, in order to load the training sets, the path is set to "../../Sets-Downsampled/TF-IDF/200/trainx_tfidf.csv" or "../../Sets-Upsampled/TF-IDF/200/trainx_tfidf.csv" with x again being a place holder for 1000, 2500, 5000
* For all model in Notebooks-Celina, in order to load the training sets, the path is set to "../../Sets-Validation/TF-IDF/200/validatex_tfidf.csv" with x again being a place holder for 1000, 2500, 5000



