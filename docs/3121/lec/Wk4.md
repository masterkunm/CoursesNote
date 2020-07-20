# Week4 lecture greedy method

## Activity selection problem

Instance: a list of activities $a_i$, $(1 \leq i \leq n)$ with starting times $s_i$ and finishing times $f_i$, No two activities can take place simultaneously.

Task: Find a maximum size subset of compatible activities.

* Attempt 1: always find the smallest one s

* Attempt 2: prefer the activity which conflicts with the fewest possible number of the remaining activities.

* The correct solutions: activities which do not conflict with the previous chosen one (and always chose the one with the earliest end time)

Proving optimality of a greedy solution:

* find the first place where the chosen activity violates the greedy choice

* show that replacing that activity with the greedy choice produces a non conflicting selection.....

* continue in the manner and "morph" this to greedy solution

## Activity selection problem2

Instance: a list of activities $a_i$, $(1 \leq i \leq n)$ with starting times $s_i$ and finishing times $f_i = s_i + d$, thus, all activities are of the same duration. No two activities can take place simultaneously.

Task: find a subset of compatible activities of maximal total duration.

Solution: Since all activities are of the same duration, this is equivalent to finding a selection with a largest number of non conflicting activities, like the previous problem.

* __if they are not the same duration, then the greedy solution no longer worked.__

## Minimizing job lateness

Instance: A start time $T_0$ and a list of jobs $a_i$, $(1 \leq i \leq n)$, with duration times $t_i$ and deadlines $d_i$. only one job can be performed at any time; all jobs have to be completed. if a job $a_i$ is completed at a finishing time $f_i \gt d_i$ then we say that it has incurred lateness $l_i = f_i - d_i$

Task: Schedule all the jobs so that the lateness of the job with the largest lateness is minimized.

Solution: Ignore job durations and schedule jobs in the increasing order of deadlines.

## tape storage

Instance: a list of n files $f_i of lengths $l_i$ which have to be stored on a tape. each file is equally likely to be needed. to retrieve a file, one must start from the beginning of the tape and scan it until the file is found and read.

Task: order the files on the tape so that the average (expected) retrieval time is minimized.

Solution: if the files are stored in order $l_1, l_2, ... l_n$, then the expected time is proportional to 

$$
l_1 + (l_1 + l_2) + (l_1 + l_2 + l_3) + ... \ + (l_1 + l_2 + ... \ + l_n) = nl_1 + (n - 1)l_2 + (n - 2)l_3 + ... \ + l_n
$$

This is minimized if $l_1 \leq l_2 \leq l_3 \leq ... \ l_n$

## Tape storage II

Instance: a list of n files $f_i$ of lengths $l_i$ and probabilities to be needed $p_i$, $\sum_{i=1}^np_i = 1$, which have to be stored on a tape. to retrieve a file, one must start from the beginning of the tape and scan it until the tape is fund and read.

Task: Order the files on the tape so that the expected retrieval time is minimized.

Solution: if the files are stored in order $l_1, l_2, ... \ l_n$, then the expected time is proportional to 

$$
p_1l_1 + (l_1 + l_2)p_2 + (l_1 + l_2 + l_3)p_3 + ... \ + (l_1 + l_2 + l_3 + ... \ + l_n)p_n
$$

this is minimized if the order of the size is descending of $l_i/p_i$ ratio.

## More practice problems for the greedy method

___common notice of greedy method: always manipulate the leftist, the shortest, the smallest.___

## the most important applications of the greedy method: the Huffman code

## greedy method applied to graph

### topological sorting

```bash
L <- empty list what will contain the sorted elements

S <- Set of all nodes with no incoming edge

while S is non-empty do

    remove a node u from S

    add u to tail of L;

    for each node v with an edge e = (u, v) from u to v do

        remove edge e from the graph

        if v has no other incoming edges then insert v into S

if graph has edges left, then return error (graph has at least on cycle) else return L (a topologically sorted order)
```

## greedy method applied to graphs: shortest paths

### Dijkstra's shortest paths algorithm