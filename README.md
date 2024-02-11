# Triplet-Comparison-Graph-Embedding

## Overview
Welcome to the repository of my semester project on "Triplet Comparisons and Graph Embeddings".
This semester project was conducted at the [INDY Lab](https://indy.epfl.ch/) at [EPFL](https://www.epfl.ch/en/).
The project was supervised by [Prof. Matthias Grossglauser](https://people.epfl.ch/matthias.grossglauser) and [Postdoc Dr. Suryanarayana Sankagiri](https://sites.google.com/view/suryanarayana-sankagiri/home).

## Problem Statement
The problem statement of the project was to develop methods for generating accurate graph embeddings from triplet comparisons.
A triplet comparison is of the form $[i, j, k]$ where item $i$ is more similar to item $k$ than $j$ is.

We measure the accuracy of the graph embedding by the ability of the embedding to correctly infer the outcome of a new triplet comparison (implying that the embedding has captured the similarity relationships between the items).

## Approach
We developed multiple approaches to generate graph embeddings from triplet comparisons, and tested them on real-world datasets.
### 1. Generating rankings from triplet comparisons
We first generate rankings of items from triplet comparisons using the [Bradley-Terry model](https://en.wikipedia.org/wiki/Bradley%E2%80%93Terry_model).
i.e., for every target item $k$, we take all triplets of the form $[i, j, k]$ and compute the parameters $\gamma_{i|k}$, $\gamma_{j|k}$ and $\theta_j$ such that $P(i > j | k) = \frac{\gamma_{i|k}}{\gamma_{i|k} + \gamma_{j|k}}$.
The parameters are computed using a maximum likelihood estimation algorithm provided by the [`choix`](http://choix.lum.li/en/latest/).
These parameters are then used to infer a ranking of items for every target item $k$.

### 2. Generating graph embeddings from rankings
We then take these rankings and generate graph embeddings using different strategies:
- **Unweighted Graph**: We generate an unweighted graph from the rankings.
- **Weighted Graph 1**: We generate a weighted graph from the rankings, where the weight of edges is a direct function of the parameters $\gamma_{i|k}$ and $\gamma_{j|k}$.
- **Weighted Graph 2**: We generate a weighted graph from the rankings, where the weight of edges is a direct function of the parameters $\gamma_{i|k}$ and $\gamma_{j|k}$, and the degree of the nodes.
- **Weighted Graph 3**: We generate a weighted graph from the rankings, where the weight of edges is a function of the ranking of items.

## Conclusion
We tested these graph embeddings on real-world datasets and compared their performance.
The results and more information about the project can be found in the [report]

I want to thank Prof. Matthias Grossglauser and Dr. Suryanarayana Sankagiri for their guidance and support throughout the project, and I hope that the work done in this project will be useful for future research in the field of graph embeddings and triplet comparisons.
