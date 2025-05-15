# Emotion Classification in Text Messages for Sentiment Analysis
 Using Machine Learning and TF-IDF
## Dataset
(https://www.kaggle.com/datasets/nelgiriyewithana/emotions.)
"Emotions" dataset – a collection of English Twitter messages meticulously annotated with six fundamental emotions: anger, fear, joy, love, sadness, and surprise. This dataset serves as a valuable resource for understanding and analyzing the diverse spectrum of emotions expressed in short-form text on social media.
1. [Introduction](#1-introduction)
2. [Experiment Setup](#2-experiment-setup)
3. [Performance Results](#3-performance-results)
4. [Back Translation Results](#4-back-translation-results)
5. [Conclusion](#5-conclusion)
6. [References](#6-references)

## 1. Introduction
Emotion analysis in short text messages aims to classify texts based on emotional sentiment to help identify various human-related actions and events. This study uses the Emotions dataset, which contains Twitter messages labeled with six emotion categories: sadness, joy, love, anger, fear, and surprise. The analysis involves data preprocessing, feature extraction, and model training using Logistic Regression. The study focuses on exploring TF-IDF feature extraction, the impact of different feature component sizes, and class weighting on classification performance. Experimental results show that the model trained with TF-IDF features, equal class weighting, and feature components set to 6% of the total vocabulary achieves better performance.

Keywords — sentiment analysis, text, machine learning, natural language processing (NLP), logistic regression, TF-IDF

## 2. Experiment Setup

### Dataset
Contains 416,809 English-language tweets, each labeled with one of six emotion categories. Positive emotions like joy are the most frequent, while surprise is the least common. The imbalance in label distribution motivates the use of different class weighting schemes in the model.
### Preprocessing
Removing duplicates, punctuation, numbers, special characters, expanding chatwords, converting to lowercase, removing stopwords, and stemming.
### Feature Extraction
Feature Extraction: Comparison of TF and TF-IDF features with varying vocabulary component sizes.
### Classification Model
Multinomial Logistic Regression trained using the SAGA optimizer, with two class weight settings (same and balanced).
### Train-Test Split
80:20 ratio, Optimizer: SAGA, Max iterations: 1000, Regularization inverse (C): 1

## 3. Results and Analysis
Feature extraction time remained constant regardless of the number of selected vocabulary components, though memory usage increased with more features. TF-IDF features required ~1% more time than TF, but had minimal impact on overall processing time.
**Two class weighting strategies were tested:**
Same: Equal weight for each class.
Balanced: Weight inversely proportional to class frequency.
**Training time** increased with feature size and was significantly longer when using balanced class weights due to slower convergence.
**Best model:** Logistic Regression with TF-IDF features and same class weighting.
**Optimal feature size:** ~6% of total vocabulary.
**TF vs. TF-IDF: **Comparable results, with TF-IDF slightly better.
Balanced weights: Increased training time without improving accuracy.
| Feature | Class Weight | Accuracy  | Macro F1  |
| ------- | ------------ | --------- | --------- |
| TF      | Same         | 90.5%     | 87.1%     |
| TF-IDF  | Same         | **90.6%** | **87.1%** |
| TF      | Balanced     | 89.4%     | 86.4%     |
| TF-IDF  | Balanced     | 88.2%     | 84.8%     |

## 4. Conclusion
Feature extraction time is mainly affected by memory usage, not the number of selected components. TF-IDF increases extraction time by ~1%, but has little impact overall. Training time grows with feature size and is significantly longer with balanced class weights due to slower convergence. Models using same class weights perform slightly better. TF and TF-IDF offer similar performance, with TF-IDF + same weights being the most effective. The optimal feature size is around 6% of total vocabulary, balancing performance and efficiency.

## 5. References
1. Y. Wang, J. Guo, C. Yuan, and B. Li, "Sentiment Analysis of Twitter Data," *Applied Sciences*, vol. 12, no. 22, 2022.
2. N. Parveen, P. Chakrabarti, B. T. Hung, and A. Shaik, "Twitter Sentiment Analysis Using Hybrid Gated Attention Recurrent Network," *Journal of Big Data*, vol. 10, no. 50, 2023. [https://doi.org/10.1186/s40537-023-00726-3](https://doi.org/10.1186/s40537-023-00726-3)
3. N. Elgiriyewithana, "Emotions," Kaggle Dataset, Jan. 2024. [https://www.kaggle.com/datasets/nelgiriyewithana/emotions](https://www.kaggle.com/datasets/nelgiriyewithana/emotions)
4. H. A. Sayyed, S. R. Sugave, S. Paygude, B. N. Jagdale, "Study and Analysis of Emotion Classification on Textual Data," in *Proc. 6th Int. Conf. on Communication and Electronics Systems (ICCES)*, 2021. [https://doi.org/10.1109/ICCES51350.2021.9489204](https://doi.org/10.1109/ICCES51350.2021.9489204)
5. I. S. Wibowo, A. Witanti, I. Susilawati, "Keyword Extraction Judul Berita Online di Indonesia Menggunakan Metode TF-IDF," *JATISI*, 2024. [https://jurnal.mdp.ac.id/index.php/jatisi/article/download/6718/1758](https://jurnal.mdp.ac.id/index.php/jatisi/article/download/6718/1758)
6. A. K. S. Santoso, A. Noviriandini, A. Kurniasih, "Klasifikasi Persepsi Pengguna Twitter Terhadap Kasus Covid-19 Menggunakan Metode Logistic Regression," *Jurnal Informatika*, 2021. [https://repository.bsi.ac.id/repo/files/374064/download/517-1143-1-PB-ok.pdf](https://repository.bsi.ac.id/repo/files/374064/download/517-1143-1-PB-ok.pdf)
7. A. Defazio, F. Bach, S. Lacoste-Julien, "SAGA: A Fast Incremental Gradient Method With Support for Non-Strongly Convex Composite Objectives," arXiv:1407.0202, 2014. [https://arxiv.org/abs/1407.0202](https://arxiv.org/abs/1407.0202)


