# hSBM_Topicmodel

A tutorial for topic-modeling with hierarchical stochastic blockmodels using graph-tool.

Based on the works in:
- Gerlach, M., Peixoto, T. P., & Altmann, E. G. (2018). A network approach to topic models. Science Advances, 4(7), eaaq1360. https://doi.org/10.1126/sciadv.aaq1360
- C. C. Hyland, Y. Tao, L. Azizi, M. Gerlach, T. P. Peixoto, and E. G. Altmann Multilayer Networks for Text Analysis with Multiple Data Types , EPJ Data Science 10, 33 (2021). https://epjdatascience.springeropen.com/articles/10.1140/epjds/s13688-021-00288-5


## Setup

Get the code via: `git clone https://github.com/martingerlach/hSBM_Topicmodel.git`

#### Installing graph-tool

We use the [graph-tool](https://graph-tool.skewed.de/) package for finding topical structure in the word-document networks.
- see the [installation-instructions](https://git.skewed.de/count0/graph-tool/wikis/installation-instructions), where you will find packages for linux, etc.
- for linux, one relatively straightforward way is to install via conda
```
conda create --name graph-tool python=3.7
conda activate graph-tool
conda install -c conda-forge gtk3 pygobject matplotlib graph-tool
```
The packages gtk3, pygobject, matplotlib are needed to enable plotting-functionality

#### Additional packages

We need some additional packages to run the code (for example, jupyter to run the tutorial-notebooks).

The list of packages is listed in `requirements.txt`


## SBM for topic modeling of text

This method uses Stochastic block models for topic modeling of text.

#### Code

Code-base: `sbmtm.py`

Tutorial-notebook: `TopSBM-tutorial.ipynb` guides you through the different steps to do topic modeling with stochastic block models
* How to construct the word-document network from a corpus of text
* How to fit the stochastic block model to the word-document network
* How to extract the topics from the fitted model, e.g.
	* the most important words for each topic
	* the clustering of documents
	* the topic mixtures for each document
* How to visualize the topical structure, in particular the hierarchy of topics

#### Data

The example-corpus is saved in `corpus.txt`
- each line is a separate document with words separated by whitespace
- optionally, we can provide a file with titles for the documents in `titles.txt`



## Multilayer SBM for topic modeling beyond text

This method provides a multilayer extension to the Stochastic Block Model approach for topic modeling.

#### Code
The code implementing a multilayer extension to the stochastic block model has been implemented for the 2-layer SBM containing a hyperlink and text layer. The addition of a metadata layer can be done by following the process for the addition of the hyperlink layer.

Code-base: `sbmmultilayer.py`

Tutorial-notebook: `Multilayer_SBM_Tutorial.ipynb`

The tutorial notebook details how to
- Construct a multilayer SBM with the hyperlink and text layer
- Fit a multilayer SBM using simulated annealing for improved inference 
- Extract the consensus partitions from multiple runs of the fitting procedure
- Extract the topics and topic proportions associated to *blocks* of documents


#### Data
##### Wikipedia Dataset
The associated Wikipedia dataset is saved in a zip file in `data/dataset-four.zip`. 
- Contains three 3 types of data.
- Hyperlink: Each Wikipedia article has a hyperlink to another Wikipedia article.
- Text: Each Wikipedia contains text associated to it.
- Metadata: Each Wikipedia has a category assigned to it by Wikipedia users.

##### Arxiv Dataset
The arxiv-dataset contains 2542 scientific papers from the High-Energy-Physics-Theory category on arxiv with 3 types of information:
- Directed links (paper A citing paper B)
- Text (title and abstract of the paper)
- Metadata (arxiv categories of the paper)

The dataset was dervied from the "High-energy physics theory citation network" dataset (available [here](http://snap.stanford.edu/data/cit-HepTh.html)) containing 27,770 papers by filtering those papers which contain at least one category besides the High-Energy-Physics-Theory category (all papers in this dataset contain the latter category).

##### Enron Dataset

Published Enron emails with ~0.5 million emails. The data can be obtained from [here](http://snap.stanford.edu/data/email-Enron.html). It was obtained by the Federal Energy Regulatory Commission during its investigation of Enron's collapse.

The May 7, 2015 Version of dataset is uploaded here. A processed form of the Enron emails can be found [here](https://www.kaggle.com/wcukierski/enron-email-dataset).
