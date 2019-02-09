# The importance of being dissimilar in Recommendation

In recommendation scenarios, similarity measures play a fundamental role in memory-based nearest neighbors approaches. In fact, they recommend items to a user based on the similarity of either items or users in a neighborhood. In this paper, we argue that similarity between users or items, although it keeps leading importance in computing recommendations, should be paired with a value of dissimilarity (computed not just as the complement of the similarity one). We formally modeled and injected this notion in some of the most used similarity measures and evaluated our approach in a recommendation scenario showing its effectiveness with respect to accuracy and diversity results on three different datasets.

Neighborhood-based approaches have been the first family of algorithms developed for collaborative filtering recommender systems. They identify similar users or items, and they provide users with a list of items they could be interested in by exploiting the degree of similarity. To the best of our knowledge, a few works have been proposed in the past years related to asymmetric similarity, and they are mainly designed for a user-based scheme.
In this work, we investigate the effect on recommendation accuracy when we go beyond the above two assumptions and define (and include) the concepts of dissimilarity and asymmetry in similarity measures. In our proposal, we start from a probabilistic interpretation of similarity to define symmetric and asymmetric dissimilarities. The dissimilarity measures are then combined with traditional similarity values using additive and multiplicative strategies. The experimental evaluation shows that our approach outperforms the non-dissimilarity-aware counterparts improving the accuracy of results or diversity or both.

## Reference
If you publish research that uses CP-theories-SPARQL please use:
~~~
bibtex
~~~
The full paper describing the overall approach is available here [PDF](link)
The extended results that had no room in the paper are available here [ODS](https://github.com/vitowalteranelli/The-importance-of-being-dissimilar-in-Recommendation/blob/master/ImportanceOfBeingDissimilar.ods)

## Motivation
The main idea behind our proposal is that symmetric similarity may not be sufficient to capture subtle interactions between items. We assume that representing the similarity through traditional measures can lead to imperfect results as important information might not be properly considered. 
Let us consider some examples in an item-kNN scenario. Suppose we are dealing with a dataset containing rating data from the book domain on the following books: 
![Table example_books](https://github.com/vitowalteranelli/The-importance-of-being-dissimilar-in-Recommendation/blob/master/imgs/books.png)

By looking at the previous data, we see that both \textit{A Game of Thrones} and \textit{A Dance with Dragons} belong to the same saga \textit{A song of ice and fire} and they are, respectively, the first and the fifth volume. \textit{Shroud of Eternity} is the second volume of Nicci Chronicles' saga. We may assume that all the users who rated DwD also rated GoT, i.e., U DwD ⊆ U GoT. Analogously, since the topic of the book is mostly the same, we may assume that a number of readers of SoE also voted GoT, U SoE ∩ U GoT != ∅. Suppose now that we have U SoE ∩ U GoT = 20 and U Dw D ∩ U GoT = 10.. If we compute the Jaccard similarity between the pairs  SoE, GoT and DwD, GoT we have

![similarity](https://github.com/vitowalteranelli/The-importance-of-being-dissimilar-in-Recommendation/blob/master/imgs/similarity.png)

In our opinion, much relevant information has been lost in this simple example. The scenario is shown graphically in Figure 1. 
![contained](https://github.com/vitowalteranelli/The-importance-of-being-dissimilar-in-Recommendation/blob/master/imgs/smallInsideBig_.png)
a) U DwD is entirely contained in U GoT

![partially overlapped](https://github.com/vitowalteranelli/The-importance-of-being-dissimilar-in-Recommendation/blob/master/imgs/smallIntersection_.png)
b) U GoT, is partially overlapped with U SoE

It is clear that U DwD is a proper subset of U GoT and, on the contrary, there are many users in U SoE that have not experienced GoT. This information is mostly lost in the computation of the similarity values even though a piece of this information is retained in the denominator of the Jaccard coefficient through the overall value of U GoT ∪ U Dw D and U GoT ∪ U SoE. 

Under a probabilistic lens, we may define dissimilarity measures with two different probabilities:
- the probability that a generic user _u_ experienced the item _i_ but never experienced the item _j_
- the probability that a generic user _u_ experienced the item _j_ but never experienced the item _i_
Since we are introducing an asymmetric behavior in computing the similarity between _i_ and _j_ as well as between _j_ and _i_, we see that the two probabilities have a different role while computing a similarity measure.


## Credits
This algorithm has been developed by Vito Walter Anelli and Joseph Trotta while working at [SisInf Lab](http://sisinflab.poliba.it) under the supervision of Tommaso Di Noia.  

## Contacts

   Tommaso Di Noia, tommaso [dot] dinoia [at] poliba [dot] it  
   
   Vito Walter Anelli, vitowalter [dot] anelli [at] poliba [dot] it 
   
   Joseph Trotta, joseph [dot] trotta [at] poliba [dot] it 
