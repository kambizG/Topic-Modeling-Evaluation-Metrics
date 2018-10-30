# Topic Modeling Evaluation

Java implenetation of multiple evaluation metrics commonly used for evaluation of the result in topic modeling problem. The metrics are implementated following the original presentation of the algorithms in their corresponding papers.

## Coherency [1]
is used for measuring the quality of extracted topics in a topic classification solution. Given a set of documents classified into multiple similarity groups, coherency assumes that high-frequent words in each group, tend to co-occur more among the documents inside the group rather than documents across multiple groups. Thus, the higher the coherency, the better the quality of the partitioning. Based on that, the coherency is first, calculated for each similarity group in the classification result and then, the average over all individual coherency values is reported as the coherency of the classification result. In particular, given a set of documents classified into *k* topics, ![](https://latex.codecogs.com/gif.latex?T%20%3D%20%7Bt_1%2C%20t_2%2C%20...%2C%20t_k%7D), first, we calculate the coherency of each topic, *z*, with top *m* probable words, ![](https://latex.codecogs.com/gif.latex?W%5Ez%20%3D%20%5C%7Bw_1%2C%20w_2%2C%20...%2C%20w_m%5C%7D), as,

![](https://latex.codecogs.com/gif.latex?C%28z%2CW%5Ez%29%20%3D%20%5Csum_%7Bi%3D2%7D%5E%7Bm%7D%5Csum_%7Bj%3D1%7D%5E%7Bi-1%7D%5Clog%20%5Cfrac%7BD%28%7Bw_i%7D%5Ez%2C%20%7Bw_j%7D%5Ez%29%7D%7BD%28%7Bw_j%7D%5Ez%29%7D%2C)

where ![](https://latex.codecogs.com/gif.latex?D%28%7Bw_i%7D%5Ez%2C%20%7Bw_j%7D%5Ez%29) is the co-occurrence frequency of the words *v<sub>i</sub>* and *v<sub>j</sub>* among documents in *z* and ![](https://latex.codecogs.com/gif.latex?D%28%7Bw_j%7D%5Ez%29) is the total frequency of *w<sub>j</sub>* in *z*. Then, the total coherency of partitioning is calculated as follows:

![](https://latex.codecogs.com/gif.latex?C%28T%29%20%3D%20%5Cfrac%7B1%7D%7Bk%7D%20%5Ctimes%20%5Csum_%7Bz%20%5Cin%20T%7DC%28z%2C%20W%5Ez%29)

## B-Cubed [2]
is an statistical measure for evaluating the accuracy of the results of topic detection in text. It calculates the accuracy of a classification for each document compared to a ground-truth. The results can be reported either per topic as average over all documents in that topic or the whole dataset as average over all documents in the dataset. In particular, given a dataset with *n* documents, tagged with *k* hand-labels, ![](https://latex.codecogs.com/gif.latex?L%20%3D%20%5C%7Bl_1%2C%20l_2%2C%20...%2C%20l_k%5C%7D) and a classification of the documents into *k* class-labels, ![](https://latex.codecogs.com/gif.latex?C%20%3D%20%5C%7Bc_1%2C%20c_2%2C%20...%2C%20c_k%5C%7D), the B-Cubed of a document, *d*, with the hand-label *l* and the class-label *c* is calculated as:

![](https://latex.codecogs.com/gif.latex?B%28d%29%20%3D%202%20%5Ctimes%20%5Cfrac%7BP%28d%29%20%5Ctimes%20R%28d%29%7D%7BP%28d%29%20&plus;%20R%28d%29%7D%2C)

where *P* and *R* respectively stand for *Precision* and *Recall*, and are calculated as follows:

![](https://latex.codecogs.com/gif.latex?P%28d%29%20%3D%20%5Cfrac%7B%7Cd_i%7C_%7B%5Cforall%20i%3A%20i%5Cin%20c%20%2C%20i%20%5Cin%20l%7D%7D%7B%7Cd_i%7C_%7B%5Cforall%20i%3A%20i%5Cin%20c%7D%7D)

![](https://latex.codecogs.com/gif.latex?R%28d%29%20%3D%20%5Cfrac%7B%7Cd_i%7C_%7B%5Cforall%20i%3A%20i%5Cin%20c%20%2C%20i%20%5Cin%20l%7D%7D%7B%7Cd_i%7C_%7B%5Cforall%20i%3A%20i%5Cin%20l%7D%7D.)

Precision shows the likelihood of documents correctly classified as *c*, with respect to the total number of documents in *c* and recall shows that likelihood with respect to the total number of documents in *l*.

## References:

[1] [D. Mimno, H. M. Wallach, E. Talley, M. Leenders, and A. McCallum, “Optimizing   semantic   coherence   in   topic   models,”   in Proceedings of   the   Conference   on   Empirical   Methods   in   Natural   Language Processing ,  ser.  EMNLP  ’11. Stroudsburg,  PA,  USA:  Association for Computational Linguistics, 2011, pp. 262–272.](http://dl.acm.org/citation.cfm?id=2145432.2145462)

[2] [A. Bagga and B. Baldwin, “Entity-based cross-document coreferencing using the vector space model,” in Proceedings of the 17th International Conference on Computational Linguistics - Volume 1 , ser. COLING ’98. Stroudsburg, PA, USA: Association for Computational Linguistics, 1998, pp. 79–85.](http://www.aclweb.org/anthology/P98-1012)

