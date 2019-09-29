# PapersNotebook

Half a year has passed since I joined Okumura Lab, but still can't develop a focused research question. **A little of everything, nothing at all.** This repo is developed to help me dig more in the topic I'm interested with.:muscle:	

## Principles
1. Papers are roughly divided to two types: 
   * directly lead to my research topic
   * related algorithm (ML/DL)
2. 

## Catalogue

* [Subword-aligned Cross-lingual Word Embeddings](#subword-aligned-cross-lingual-word-embeddings)
  * [Cross-lingual Word Embeddings](#cross-lingual-word-embeddings)
  * [Monolingual Word Embeddings](#monolingual-word-embeddings)
  * [Subwords](#subwords)

## Subword-aligned Cross-lingual Word Embeddings

### Cross-lingual Word Embeddings

* [A Survey of Cross-lingual Word Embedding Models](https://arxiv.org/pdf/1706.04902.pdf)

#### Introduction

1. Cross-lingual Embeddings as Extensions: 
   - monoligual vector representations --> cross-lingual vector representations (in a joint embedding space) 
   ![](./images/cross-lingual-embedding.png)  
   - bilingual approaches --> multilingual setting

2. Data Requirements: 
   - alignment: word / sentence / document  
   - parallel / comparable ( about the same topic)
   
3. Obejective Functions 

4. Values:  
   - compare meaning of words across languages
   - mode transfer between languages (resource-rich --> low-resource, through common representation space), can also be evaluation.

#### [Monolingual Embedding Models](#monolingual-word-embeddings)

 
#### Cross-lingual Representations before Embeddings
#### Typology
#### Alignment
* Approaches
  * mapping-based
  * pseudo-bilingual corpora based
  * hybrid / joint 
* word


* [Unsupervised Cross-lingual Word Embeddings Based on Subword Alignment](http://www.tkl.iis.u-tokyo.ac.jp/new/uploads/publication_file/file/911/cicling2019.pdf)

Unluckily, it seems the idea of **using subword information in cross-lingual word embedding** has already been published by [Jin SAKUMA](http://www.tkl.iis.u-tokyo.ac.jp/~jsakuma/) of Yoshinaga Lab in U-Tokyo. **Need careful look to see what future work can be done while remain originality**.(2019/09/28)


* [Improving Cross-Lingual Word Embeddings by Meeting in the Middle](https://aclweb.org/anthology/D18-1027)

* [Unsupervised Cross-lingual Transfer of Word Embedding Spaces](https://aclweb.org/anthology/D18-1268)

### Monolingual Word Embeddings

* LSA: [Indexing by Latent Semantic Analysis](http://lsa.colorado.edu/papers/JASIS.lsi.90.pdf)  
1. factorize sparse word-word co-occurance matrix **C** --> dense word representations

2. TF-IDF (Term Frequency-Inverse Document Frequency):
![TF-IDF](https://www.google.com/url?sa=i&source=images&cd=&ved=2ahUKEwikiNbW5_XkAhUKPXAKHQ-3BakQjRx6BAgBEAQ&url=https%3A%2F%2Fwww.link-assistant.com%2Fnews%2Ftf-idf-tool-for-seo.html&psig=AOvVaw3SMhnLMHGgaTq-da_oEal5&ust=1569838481144190)
   - weighting, more frequently a word in a documnet, more important; more docunments the word in, less important.   
   - no location/context information
* CBOW:
* SGNS: 
* GloVe: 


