# PapersNotebook

Half a year has passed since I joined Okumura Lab, but still can't develop a focused research question. **A little of everything, nothing at all.** This repo is developed to help me dig more in the topic I'm interested with.:muscle:	

## Principles
> まず努力しなさい。人の倍の量の文献を採集し、その定理全てに目を通しなさい (**証明は後から読んでも構いません**)。各々の文献の間の相互の関係を理解しなさい。そして、文献をしまい、瞑想し、頭の中に入っている (読んだ文献の) 内容だけで、何ができるか、そして何ができそうかについて考えなさい。学会などで人の話を聞きなさい。**アイデアが思いついたら、再び文献を読み直したり、**新たな文献を集めて、その問題が解けるかどうかを判断しなさい。解けないならば、**何が欠けていて解けないのか**を見究めなさい。そして、この過程をノートに書き留めて、**ときどき読み返しなさい**。  
> [「研究読本」 植松友彦先生](http://www.it.ce.titech.ac.jp/uyematsu/howtoresearch.pdf)  

1. Papers are roughly divided to two types: 
   * directly lead to my research topic
   * related algorithm (ML/DL)
2. Intensive reading of papers of 2nd level (references of 1st level) are in /2nd directory, while anchored in this document.

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

2. Data Requirements (choice of bilingual supervision signal): 
   - alignment (align a cross-lingual representation space): word / sentence / document  
   - parallel (exact translation) / comparable (about the same topic, only similar in some way)
   ![nature and alignment](./images/nature-and-alignment.png)
   
3. Obejective Functions 

4. Values:  
   - compare meaning of words across languages, provide fine-grained word-level links between languages
   - mode transfer between languages (resource-rich --> low-resource, through common representation space), can also be evaluation  
     - cross-lingual knowledge transfer: cross-lingual parser transfer
       
   - boost syntactic parsing, POS tagging, semantic role labeling, by relying on shared lexical information  
   - advantages in neural network: continuous representations can be directly plugged into end-to-end neural architectures as sets of lexical features.

#### [Monolingual Embedding Models](#monolingual-word-embeddings)

 
#### Cross-lingual Representations before Embeddings (History)

- pre-date word embedding ideas
  - data: seed lexica / parallel data / document-aligned data
  - traditional context counting  
   [Cross-lingual Induction of Selectional Preferences(2010)](https://www.aclweb.org/anthology/N10-1135)  

   [Bootstrapping Unsupervised Bilingual Lexicon Induction(2017)](https://www.aclweb.org/anthology/E17-2098)
  - learning from limited bilingual supervision, **word pairs from seed bilingual lexicons**  
    using **seed** bilingual dictionary  
   [Bilingual Lexicon Extraction from Comparable Corpora Using Label
Propagation](https://www.aclweb.org/anthology/D12-1003)  
    predecessor to cross-lingual word embedding models
  - cosine similarity --> word translation probabilities  
   [**A Strong Baseline for Learning Cross-Lingual Word Embeddings
from Sentence Alignments(2017)**](https://www.aclweb.org/anthology/E17-1072)  
    greedy decoding algorithm
  

  
- language-independent representations
  - rely on abstract linguistic labels, not lexical features (delexicalized cross-lingual and domain transfer)
  - rely on syntactic/POS contexts(2015) 
  * [How to (Properly) Evaluate Cross-Lingual Word Embeddings:
  On Strong Baselines, Comparative Analyses, and Some Misconceptions](https://www.aclweb.org/anthology/P19-1070)

#### Typology

> for final performance: choice of data \> underlying architecture
* after carefully chosen data, fine-grained optimized by architecture/hyper-parameters/fine-tuning
* [Cross-lingual Models of Word Embeddings: An Empirical Comparison](https://www.aclweb.org/anthology/P16-1157)

#### Approaches
* mapping-based
* pseudo-bilingual corpora based 
  1. merge aligned document pairs
  2. apply a monolingual representation model on top of the merged data  
  --> pseudo-cross-lingual
* hybrid / joint 

#### Alignment: detailed disscussed in the following sections

* [word](#word-level-alignment)
  - parallel
    - using bilingual/cross-lingual dictionary
      - automatically align words in a parallel corpus -> produce bilingual dictionary
        
        
  - comparable
    - need other modalities: images
    
* sentence
  - parallel
    - Europarl corpus (parliament text)
  - comparable
    - captions of **same** images
    - different languages in **similar** images (not translations)

* document (comparable)
    - parallel requires translations, rare
    - **topic-aligned**: Wikipedia  
      multilanguage probabilistic topic modeling  
      topic distributions  
      shared topical spaces  
     [Inverted indexing for cross-lingual NLP](https://zeljkoagic.github.io/publications/sogaard2015-inverted.pdf)  
    - **class aligned**: sentiment analysis / multi-class classification
    

* subword 
  * [**Unsupervised Cross-lingual Word Embeddings Based on Subword Alignment**](http://www.tkl.iis.u-tokyo.ac.jp/new/uploads/publication_file/file/911/cicling2019.pdf)

  Unluckily, it seems the idea of **using subword information in cross-lingual word embedding** has already been published by [Jin SAKUMA](http://www.tkl.iis.u-tokyo.ac.jp/~jsakuma/) of Yoshinaga Lab in U-Tokyo. **Need careful look to see what future work can be done while remain originality**.(2019/09/28)


* [Improving Cross-Lingual Word Embeddings by Meeting in the Middle](https://aclweb.org/anthology/D18-1027)

* [Unsupervised Cross-lingual Transfer of Word Embedding Spaces](https://aclweb.org/anthology/D18-1268)

### Word-level Alignment
Two concepts first:  
* Bilingual lexicon induction  
  by nearest neighbour embeddings
* Hubness: 
  a phenomenon observed in high-dimensional spaces
  hubs are nearest neighbours of many other points

Three methods:
* [Mapping-based](#mapping-based-method)
  1. train monoligual word representations independently
  2. learn a transformation matrix
* Pseudo-multi-lingual corora-based
  1. automatically constructed copora containing words from both source and target
  2. use monolingual word embeddings on the copora
* Joint:
  1. take parallel text
  2. minimize monolingual losses of source and target languages, jointly with cross-lingual regularization term


Mapping-based Method: **to learn a mapping**  

Differ along multiple dimensions:  
* mapping method
* seed lexicon used to learn the mapping
* refinement
* retrieval of nearest neighbours

Four types:
* Regression: map embeddings in source to target space, maximizing similarity
  - **similar geometric constellations**, possible to learn a linear projection
  - seed words: 5000 most frequent word pairs  
    objective function: Euclidean distance(mean sqaures error, MSE)
    optimization: [stochastic gradient descent](#stochastic-gradient-descent)
* Orthogonal: regression + orthogonal transformation
* Canonical: map both to a new shared space
* Magin: maximize the margin between the correct and other candidates




  
  

### Monolingual Word Embeddings

* LSA: [Indexing by Latent Semantic Analysis](http://lsa.colorado.edu/papers/JASIS.lsi.90.pdf)

> factorize sparse word-word co-occurance matrix **C** --> dense word representations  

1. elements(co-occurence counts) in **C** usually be replaced by the following for different purposes
    
   - TF-IDF (Term Frequency-Inverse Document Frequency):  
![TF-IDF](https://www.link-assistant.com/images/news/tf-idf-tool-for-seo/screen-03.png)  
     - weighting, more frequently a word in a documnet, more important; more docunments the word in, less important.     
     - no location/context information
   - PMI (pointwise mutual information):  
  ![PMI](https://latex.codecogs.com/gif.latex?PMI(w_{i},w_{j})&space;=&space;log\frac{p(w_{i},w_{j})}{p(w_{i})p(w_{j})}=log\frac{count(w_{i},w_{j})count(corpus)}{count(w_{i}),count(w_{j})})  
     - variant TF-IDF, biased by number of words itself (some high-frequency words like "the")
     - unobserved word, PMI = log0 = ∞, set to 0
  
2. factorize PMI matrix **P** using SVD(Singular Value Decomposition)  
   - U, V column orthonormal, \psi diagonal singular  
    ![PMI-SVD](https://latex.codecogs.com/gif.latex?P&space;=&space;U\psi&space;V^{T})
   
   
3. reduce embedding matrix X to dimensionality k  
   - \psi-k: top k singular values, U-k: corresponding columns  
    ![k-PMI](https://latex.codecogs.com/gif.latex?X&space;=U_{k}\psi&space;_{k})  
    

* MML(Max-margin loss): [A Unified Architecture for Natural Language Processing:
Deep Neural Networks with Multitask Learning](https://ronan.collobert.com/pub/matos/2008_nlp_icml.pdf)
  - vocabulary: list of words; corpus: set of texts 
  - may expand later (2019/09/29) 

* CBOW(Continuous bag-of-words):
> predict the center word  from all context words, n predict 1

* Skip-gram: 
> predict each context word from center word, 1 predict n
  - optimizations
    1. Hierarchical Softmax:
       - output layer: using haffman tree
    
  **2. Negative Sampling:**   
  
    * [Distributed Representations of Words and Phrases and their Compositionality](./2nd/Distributed-Representations-of-Words-and-Phrases-and-their-Compositionality.md)
        
    * [Improving Distributional Similarity with Lessons Learned from Word Embeddings](https://www.aclweb.org/anthology/Q15-1016)


* GloVe: 


### Subwords
* [**Bilingual Lexicon Induction by Learning to Combine Word-Level and
Character-Level Representations(2017)**](https://www.aclweb.org/anthology/E17-1102)
 

## Stochastic Gradient Descent
### Gradient Descent
suppose a loss function
![loss-function](https://latex.codecogs.com/gif.latex?J(\theta&space;)&space;=&space;\frac{1}{2}\sum&space;(h_{\theta&space;}(x)-y)^{2})  
![h_x](https://latex.codecogs.com/gif.latex?h_{\theta&space;}(x)&space;=&space;\theta&space;_{0}&plus;\theta&space;_{1}x_{1}&plus;...&plus;\theta&space;_{n}x_{n})  
![loss-function](https://latex.codecogs.com/gif.latex?J(\theta&space;)&space;=&space;\frac{1}{2}\sum&space;(h_{\theta&space;}(x)-y)^{2})  
simply you can directly solve an equation about derivative = 0， but when high dimensional, may not solvable.  

