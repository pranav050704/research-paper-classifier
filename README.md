# Research Paper Classification

A machine learning project that classifies research paper abstracts into three categories: **Science, Business, and Social Science**. The project compares multiple classification algorithms, evaluates their performance, and provides a PDF-based prediction demo in a Jupyter Notebook.

## Project Overview

Research papers cover many domains, making automatic categorization useful for organizing and exploring academic literature. This project uses Natural Language Processing (NLP) and supervised machine learning to predict a category from a paper's abstract.

## Objectives

- Prepare a labeled dataset of research paper abstracts.
- Clean and preprocess text data.
- Convert text into numerical features using TF-IDF.
- Train and compare six baseline classification algorithms.
- Tune selected models using GridSearchCV.
- Evaluate performance using accuracy, precision, recall, F1-score, and confusion matrices.
- Demonstrate prediction on a research paper PDF.

## Categories

The classifier predicts one of the following labels:

- **Science**
- **Business**
- **Social Science**

## Models

1. Logistic Regression
2. Decision Tree
3. Multinomial Naive Bayes
4. K-Nearest Neighbors (kNN)
5. Support Vector Machine (SVM)
6. Random Forest

### Hyperparameter tuning

GridSearchCV with five-fold cross-validation and macro F1-score was used to tune selected models:

- Logistic Regression
- Support Vector Machine
- Random Forest

TF-IDF vectorization is included inside the tuning pipelines to avoid fitting the vectorizer on validation folds.

## Dataset

The dataset was assembled from research-paper metadata and abstracts collected from Scopus exports.

After cleaning, deduplication, and removal of selected ambiguous records, the working dataset contains **1,183 abstracts**:

| Category | Number of abstracts |
|---|---:|
| Science | 396 |
| Business | 392 |
| Social Science | 395 |
| **Total** | **1,183** |

The dataset was split into training and testing sets using an 80:20 stratified split with `random_state=42`.

**Dataset access:** The raw dataset files are maintained locally and are not included in this repository. Obtain and use the data only in accordance with the applicable database, publisher, and licensing terms.

## Text Preprocessing

The notebook performs text cleaning and preprocessing, including:

- Lowercasing text and removing punctuation.
- Removing stopwords while preserving negation terms such as `not`, `no`, and `nor`.
- Lemmatizing words using part-of-speech information where available.
- Converting text into numerical features using TF-IDF.

## Evaluation

Models are evaluated on the held-out test set using:

- Accuracy
- Macro precision
- Macro recall
- Macro F1-score
- Confusion matrices

The notebook includes a model comparison chart and confusion matrices for the baseline and tuned models.

### Selected results

| Model | Test accuracy |
|---|---:|
| Logistic Regression (Baseline) | 79.75% |
| Decision Tree (Baseline) | 75.95% |
| Multinomial Naive Bayes (Baseline) | 78.06% |
| kNN (Baseline) | 71.31% |
| SVM (Baseline) | 82.28% |
| Random Forest (Baseline) | 80.59% |
| Logistic Regression (Tuned) | 86.50% |
| SVM (Tuned) | 85.65% |
| Random Forest (Tuned) | 84.81% |

The tuned Logistic Regression model achieved the highest test accuracy among the configurations listed above. These results apply to the current dataset split and should not be interpreted as a guarantee of performance on every research paper.

## Prediction Demo

The Jupyter Notebook includes a demonstration that:

1. Accepts an uploaded research paper PDF.
2. Extracts text from the PDF.
3. Attempts to identify the abstract section.
4. Passes the extracted abstract to the tuned Logistic Regression pipeline.
5. Displays the predicted category.


**Limitations of demo:** Abstract extraction depends whether the text is selectable. Scanned documents(images) may require OCR. Predictions are model estimates and should be checked against the paper's actual subject.

## Requirements

The project uses Python and the following main libraries:

- pandas
- NumPy
- Matplotlib
- scikit-learn
- NLTK
- PyPDF2
- ipywidgets
- Jupyter

## Future Improvements

- Improve abstract extraction for different PDF layouts.
- Add support for Word documents (`.docx`).
- Improve evaluation using additional datasets and cross-validation.
- Develop a standalone user interface if required.

## Author

**Pranav Makwana**

M.Tech in Artificial Intelligence  
Indian Institute of Technology Roorkee

GitHub: [pranav050704](https://github.com/pranav050704)
