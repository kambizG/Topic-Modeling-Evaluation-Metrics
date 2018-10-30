# Topic Modeling Evaluation

Java implenetation of multiple evaluation metrics commonly used for evaluation of the result in topic modeling problem. The metrics are implementated following the original presentation of the algorithms in their corresponding papers.

## Coherence Score
Coherency is used for measuring the quality of extracted topics in a topic classification solution. Given a set of documents classified into multiple similarity groups, coherency assumes that high-frequent words in each group, tend to co-occur more among the documents inside the group rather than documents across multiple groups. Thus, the higher the coherency, the better the quality of the partitioning. Based on that, the coherency is first, calculated for each similarity group in the classification result and then, the average over all individual coherency values is reported as the coherency of the classification result. In particular, given a set of documents classified into *k* topics, ![](https://latex.codecogs.com/gif.latex?T%20%3D%20%7Bt_1%2C%20t_2%2C%20...%2C%20t_k%7D), first, we calculate the coherency of each topic, *z*, with top *m* probable words, ![](https://latex.codecogs.com/gif.latex?W%5Ez%20%3D%20%5C%7Bw_1%2C%20w_2%2C%20...%2C%20w_m%5C%7D), as,

![](https://latex.codecogs.com/gif.latex?C%28z%2CW%5Ez%29%20%3D%20%5Csum_%7Bi%3D2%7D%5E%7Bm%7D%5Csum_%7Bj%3D1%7D%5E%7Bi-1%7D%5Clog%20%5Cfrac%7BD%28%7Bw_i%7D%5Ez%2C%20%7Bw_j%7D%5Ez%29%7D%7BD%28%7Bw_j%7D%5Ez%29%7D%2C)

where ![](https://latex.codecogs.com/gif.latex?D%28%7Bw_i%7D%5Ez%2C%20%7Bw_j%7D%5Ez%29) is the co-occurrence frequency of the words *v<sub>i</sub>* and *v<sub>j</sub>* among documents in *z* and ![](https://latex.codecogs.com/gif.latex?D%28%7Bw_j%7D%5Ez%29) is the total frequency of *w<sub>j</sub>* in *z*. Then, the total coherency of partitioning is calculated as follows:

![](https://latex.codecogs.com/gif.latex?C%28T%29%20%3D%20%5Cfrac%7B1%7D%7Bk%7D%20%5Ctimes%20%5Csum_%7Bz%20%5Cin%20T%7DC%28z%2C%20W%5Ez%29)

Reference: [D. Mimno, H. M. Wallach, E. Talley, M. Leenders, and A. McCallum, “Optimizing   semantic   coherence   in   topic   models,”   in Proceedings of   the   Conference   on   Empirical   Methods   in   Natural   Language Processing ,  ser.  EMNLP  ’11. Stroudsburg,  PA,  USA:  Association for Computational Linguistics, 2011, pp. 262–272.](http://dl.acm.org/citation.cfm?id=2145432.2145462)

## B-Cubed F-Score
