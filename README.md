# hSBM_Topicmodel

A tutorial for topic-modeling with hierarchical stochastic blockmodels using graph-tool.

Based on the works in:
- Gerlach, M., Peixoto, T. P., & Altmann, E. G. (2018). A network approach to topic models. Science Advances, 4(7), eaaq1360. https://doi.org/10.1126/sciadv.aaq1360


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

This method provides a multilayer extension to the stoachstic block model approach for topic modeling.

#### Code

Code-base: `sbmmultilayer.py`

Tutorial-notebook: `Multilayer_SBM_Tutorial.ipynb`
