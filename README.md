# Notebook NLP
* [Notebook Alex - Press here to open it in Colab](https://colab.research.google.com/github/AlexSperka/Kaggle_Challange_NLP_Disaster_Tweets/blob/master/nlp_colab_notebook_V1.ipynb)

# Introduction

---
[This notebook](https://www.kaggle.com/alexs2020/bert-1024-and-distilbert-comparison) shows my approach for the classification of desaster tweets regarding the [NLP Twitter kaggle challange]( https://www.kaggle.com/c/nlp-getting-started/overview).

My initial idea was to compare several BERT implementations with each other ([BERT Uncased 1024](https://tfhub.dev/tensorflow/bert_en_uncased_L-24_H-1024_A-16/2), [BERT Uncased 768](https://tfhub.dev/tensorflow/bert_en_uncased_L-12_H-768_A-12/2), [DistilBERT](https://huggingface.co/distilbert-base-uncased)) to get a feeling how well they performe given the task of the kaggle challange. For this, reasearch was done by getting used to the [BERT paper](https://arxiv.org/pdf/1810.04805v2.pdf) to understand the basic foundations of the algorithm as well as the tokenizer. This [colab notebook ](https://colab.research.google.com/github/jalammar/jalammar.github.io/blob/master/notebooks/bert/A_Visual_Notebook_to_Using_BERT_for_the_First_Time.ipynb#scrollTo=q1InADgf5xm2) which is trying to visualize some things was a great inspiration and helped a lot to setup my initial notebook.

---
This notebook is seperated into different sections, relating to the common data science workflow (except the hypothesis and data collection where already done). 

1.   Setup and Check Infrastructure
2.   Having a first look at the Data (EDA)
3.   Helper Functions for Data Cleaning
4.   Data Cleaning (Feature Engineering)
5.   Pre-trained Bert Uncased model 1024 (& 768) (Model building 1/2)
6.   Pre-trained DistilBert model ((Model building 2/2)
7.   Showing Confusion Matrices for BERT models (to compare / evaluate)

---


## Approach:

I started with common values mentioned in different notebooks on kaggle (see inspiration in first section) to get a feeling what influences what and how does it generelly work. After gaining some experience I combined several approaches from the notebooks and general information from the internet. The most promising was one relatively at the beginning with a kaggle score of 84.247% (userID: AlexS2020, rank: 116 at 14.09.2020). This involved a relatively simple notebook running on kaggle, using the parameters mentioned in the list in section 5. It was not possible for me to beat this afterwards, although I tried a lot of different ways and optimizations (added apprevations, cleaned only partly, left links in the tweets, emojis, ...).

## Evaluation:
As will be mentioned in the last section, I used to compare the different val_acc and loss values of different models as well as uploading the submission files to get a direct comperision via the score. Last step to evaluate are the confusion_matrices to see how many false positive/negative and true postivie/negative.

## Conclusion:
Overall it was an interesting project / competition which enabled me to learn new stuff and try out several tools. It is interesting to see, that the lightweight DistilBERT model is relatively competitive to the way larger BERT 1024 model and the scores do not differ that much. This gets even more interesting when comparing the runtime the 1024 model needs in an equal setup 1458 seconds per epoche, the DistilBERT just 248 seconds (with almost same results after one epoche, see the confusion matrices)!

Last learning for today: DistilBERT tends to overfit when using higher learning rates and more epochs way faster then the BERT 1024 model.

## Outlook:
There are several ways how to improve these scores from my point of view. Some of them can be seen in other notebooks already (especially the larger ones).

1.   Run the notebook on larger hardware to play around with larger batch_sizes>16 and larger len_max>160.
2.   Adding dropouts to fight the overfitting
3.   Using different models behind each other as mentioned in the BERT paper to optimize output
4.   Modify the uncased model of BERT with more/different layers and play around with different activation functions, here for example: https://www.kaggle.com/sokolheavy/multi-dropout-aug-oof
5.   Write a script on local machine running different learning rates and other parameters so that different optimas can be found. 
6.   An adaptive learning rate could also help with optimizing the results

## Limitations:
- Some of the points mentioned in Outlook were not possible since running code in browser + only 36h GPU-time per week is hardly enough
- Automation of parameter search not feasible
- Getting OOR erros quite offen due to limited GPU storage (its quite big for free use case, still...)

---
