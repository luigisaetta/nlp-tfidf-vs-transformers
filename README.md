# NLP and Sentiment Analysis: TF-IDF vs Transformers
In this repo I have collected all the code developed to test the **transformers approach vs tf-idf**

I've developed models for Sentiment Analysis. 

## Dataset
The dataset used is the **Internet Movie Dataset (IMdb)**:
a collection of 50000 feedbacks divided in two categories: 0= negative, 1=positive)

The dataset can be downloaded from here: 

http://ai.stanford.edu/~amaas/data/sentiment/

after the download it can be decompressed with this command:

tar -zxf aclImdb_v1.tar.gz

I have used this dataset because **it has been widely used to show how to apply ML to Text analysis**.

## Bags-of-words and TF-IDF
The simplest approach to use ML on Text data is to consider a text as "a bag of words".

In other words, to build a feature vector out of the text we:
* build a list of words to track (a dictionary)
* count the occurence of each word in the text
* scale this value to avoid that common words (a, an, the...) have the biggest importance

Term Frequency (TF) is the simple count of the word occurrence in each document. Inverse Document Frequency (IDF) is one way to scale.

Well, a very good and detailed explanation can be found, for example, in the book from S. Raschka:

[Python Machine Learning](https://www.amazon.it/Python-Machine-Learning-scikit-learn-TensorFlow/dp/1789955750/ref=sr_1_1?__mk_it_IT=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=1VB5VPMTQ9D5&keywords=Python+Machine+Learning&qid=1651399178&sprefix=python+machine+learning%2Caps%2C87&sr=8-1)

in chap. 8.

The approach based on TF-IDF is explored in my notebook:

https://github.com/luigisaetta/nlp-tfidf-vs-transformers/blob/main/imdb_tf_idf.ipynb

## Transformers
Obviously, I have used the **Transformers library** from **HuggingFace**.

The model I have used is: "distilbert-base-uncased", that is transparently downloaded from the HF Hub.

Some details regarding my custom tuning:
* MAX_LENGTH = 300
* to be independent from the train/validation split, I have used k-fold cv (folds = 5)
* EPOCHS = 3

on a P100 GPU the entire training process takes around **150 mins**.

all the details needed for fine tuning distilbert on a custom dataset can be found, with a clear explanation, in chap. 2 of the book:

[Natural Language Processing with Transformers](https://www.amazon.it/Natural-Language-Processing-Transformers-Applications/dp/1098103246/ref=tmm_pap_swatch_0?_encoding=UTF8&qid=1651396765&sr=8-2)

from O' Reilly (I greatly recommend reading this book!)

The approach based on Transformers is explored in my notebook:

https://github.com/luigisaetta/nlp-tfidf-vs-transformers/blob/main/train1-kfold-distilbert.ipynb

## Other works
As you can easily image the subject has already been explored and you can find several papers or works on Internet (even if not too many)

For example, in this paper https://arxiv.org/pdf/2005.13012.pdf the authors compare results obtained using a **BERT fine-tuned model** (see section 4.1) with a TF_IDF model.

Their results:
* BERT : ACC = 0.939
* TF_IDF + Multinomial NB: ACC = 0.877

## Citations
@InProceedings{maas-EtAl:2011:ACL-HLT2011,
  author    = {Maas, Andrew L.  and  Daly, Raymond E.  and  Pham, Peter T.  and  Huang, Dan  and  Ng, Andrew Y.  and  Potts, Christopher},
  title     = {Learning Word Vectors for Sentiment Analysis},
  booktitle = {Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies},
  month     = {June},
  year      = {2011},
  address   = {Portland, Oregon, USA},
  publisher = {Association for Computational Linguistics},
  pages     = {142--150},
  url       = {http://www.aclweb.org/anthology/P11-1015}
}

