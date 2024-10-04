
# Fake News Classification Project

This project aims to classify fake and real news using the **WELFake Dataset**. The analysis includes preprocessing, vectorization, classification using Logistic Regression, and topic analysis through Non-Negative Matrix Factorization (NMF).

## Access the Report

The complete report of the analysis is available in PDF format and can be accessed [here](https://github.com/lorrancmlopes/Fake-News-Classification/blob/main/report.pdf).

## Getting Started

### Step 1: Download the Dataset

You need to download the **WELFake Dataset** from Kaggle. Follow these steps:

1. Go to [Fake News Classification Dataset on Kaggle](https://www.kaggle.com/datasets/saurabhshahane/fake-news-classification).
2. Download the dataset and save it in the `data` folder of this project.

### Step 2: Set Up the Environment

1. Create a virtual environment:
   ```bash
   python -m venv env
   ```

2. Activate the virtual environment:
   - On Windows:
     ```bash
     .\env\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source env/bin/activate
     ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Step 3: Run the Analysis

After setting up the environment, you can run the Jupyter notebook for analysis:

1. Navigate to the `notebooks` folder and open `analysis.ipynb`.
2. Run the notebook to perform the classification and topic analysis.

## Project Overview

### Dataset
We used the **WELFake Dataset** from Kaggle, which contains approximately 72,000 articles for fake news detection, sourced from multiple datasets.

### Classification Pipeline

The pipeline includes the following steps:
- **Preprocessing**: Tokenization, stopword removal, and lemmatization using NLTK.
- **Vectorization**: Text is converted to numerical form via TF-IDF Vectorizer.
- **Classification**: Logistic Regression is used, with coefficients indicating word importance.

### Evaluation

We evaluated the model's performance using both a single train-test split and 5-fold cross-validation. The accuracy on the initial test set was **95.17%**, and across 5-fold cross-validation, the model achieved a mean accuracy of **95.23%**.

![image](https://github.com/user-attachments/assets/cf61d12a-1fd7-4337-b0d6-a5b18fc57ffe)


#### Important Words:
- **Fake News**: Words like "via," "us," and "hillary" were key indicators, but over-reliance on structural elements (e.g., "via," "com") could lead to misclassifications.
- **Real News**: Words like "reuters," "said," and "but" indicated real news, reflecting journalistic language and attribution to reputable sources.

### Dataset Size

Following the learning curves from [3], we found that expanding the dataset beyond 20,000–25,000 samples leads to diminishing returns in accuracy, as the testing error stabilizes.

![image](https://github.com/user-attachments/assets/938eef87-da74-4a88-a19f-c9fa06ab5dd8)

![image](https://github.com/user-attachments/assets/ca62d95c-eaab-4570-89b0-abc0acb7cd2d)


### Topic Analysis

To analyze the topics in the dataset, we applied Non-Negative Matrix Factorization (NMF) on the document-term matrix. Five distinct topics were identified, and the results show that classification accuracy varies across topics. Topics related to **US politics** and **official investigations** achieved the highest accuracy (above 96%), while more generic topics, such as those using common terms like "people" and "know," had lower accuracy (around 93%).

The two-layer classifier, which first classifies by topic using NMF and then uses Logistic Regression for topic-specific classification, performed similarly to the single-layer model but provided more insights into the topic-based variations in classification performance.

## References

1. P. K. Verma, P. Agrawal, I. Amorim, and R. Prodan, "WELFake: Word embedding over linguistic features for fake news detection,'' *IEEE Transactions on Computational Social Systems*, vol. 8, no. 4, pp. 881–893, 2021. doi: 10.1109/TCSS.2021.3068519.
2. J. S. Cramer, "The Origins of Logistic Regression,'' Tinbergen Institute Working Paper No. 2002-119/4, Dec. 2002. Available at SSRN: https://ssrn.com/abstract=360300 or http://dx.doi.org/10.2139/ssrn.360300.
3. C. Cortes, L. D. Jackel, S. A. Solla, V. Vapnik, and J. S. Denker, "Learning curves: Asymptotic values and rate of convergence,” in *Advances in Neural Information Processing Systems (NIPS)*, 1993, pp. 327–334.

