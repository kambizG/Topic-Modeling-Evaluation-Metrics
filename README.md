# Topic Modeling Evaluation

Java implenetation of multiple evaluation metrics commonly used for evaluation of the result in topic modeling problem. The metrics are implementated following the original presentation of the algorithms in their corresponding papers.

## Coherence Score
Coherency is used for measuring the quality of extracted topics in a topic classification solution. Given a set of documents classified into multiple similarity groups, coherency assumes that high-frequent words in each group, tend to co-occur more among the documents inside the group rather than documents across multiple groups. Thus, the higher the coherency, the better the quality of the partitioning. Based on that, the coherency is first, calculated for each similarity group in the classification result and then, the average over all individual coherency values is reported as the coherency of the classification result. In particular, given a set of documents classified into $k$ topics, $T = \{t_1, t_2, ..., t_k\}$, first, we calculate the coherency of each topic, $z$, with top $m$ probable words, $W^z = \{w_1, w_2, ..., w_m\}$, as,
$$C(z,W^z) = \sum_{i=2}^{m}\sum_{j=1}^{i-1}\log \frac{D({w_i}^z, {w_j}^z)}{D({w_j}^z)},$$

where ![image](https://latex.codecogs.com/gif.latex?D%28%7Bw_i%7D%5Ez%2C%20%7Bw_j%7D%5Ez%29) is the co-occurrence frequency of the words $v_i$ and $v_j$ among documents in $z$ and $D({w_j}^z)$ is the total frequency of $w_j$ in $z$. Then, the total coherency of partitioning is calculated as follows:

![equation](https://latex.codecogs.com/gif.latex?C%28T%29%20%3D%20%5Cfrac%7B1%7D%7Bk%7D%20%5Ctimes%20%5Csum_%7Bz%20%5Cin%20T%7DC%28z%2C%20W%5Ez%29)



## B-Cubed F-Score
