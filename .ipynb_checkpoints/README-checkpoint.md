# NLP and Sentiment Analysis: TF-IDF vs Transformers
In this repo I have collected all the code developed to test the transformers approach vs tf-idf

I've developed some model for Sentiment Analysis. 

## Dataset
The dataset used is the **Internet Movie Dataset (IMdb)**:
a collection of 50000 feedbacks divided in two categories: 0= negative, 1=positive)

The dataset can be downloaded from here: 

http://ai.stanford.edu/~amaas/data/sentiment/

after the download it can be decompressed with this command:

tar -zxf aclImdb_v1.tar.gz

I have used this dataset because **it has been widely used to show how to apply ML to Text analysis**.

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

