###Third Experiment - (Test under heavy load)

Our final experiment was to test neo4j under heavy query load. For this purpose we ‘ve developed the following python script (this script is sent along with these experiment results):

![3-1](https://cloud.githubusercontent.com/assets/11991105/20260854/1956989c-aa64-11e6-8f5d-9221c816acef.png)

The idea is to open a large number of connections (1000 connections) by utilizing many threads, and ask for different parts of our db graph.
In neo4j, each node has an <id> element. We already have hundreds of millions of nodes, so each time we pick a random id, and we ask for this node. With this way, we will issue many cache misses, as each time we ask for a different portion of our graph.
Next, we'll evaluate the same queries while neo4j is under heavy query load (1000 simultaneous connections).

1 Give me all the methods declared on the Repository xxx?

![3-2](https://cloud.githubusercontent.com/assets/11991105/20260924/5fed9db4-aa64-11e6-9ce1-9310ca365c7e.png)

We've noticed serious delay this time, which is caused by the large number of open connections / concurrent queries. We get back 3385 rows in 7719 ms (as opposed to 2800 ms when there is just one connection /query)

2 Give me all the parameters of the method xxx?

![3-3](https://cloud.githubusercontent.com/assets/11991105/20260977/93e6a016-aa64-11e6-8d8d-e760e3ba12d9.png)

Again, we notice a big delay. 610 ms (as opposed to 74 ms)  to execute, to return 1 row.

3 Give me all the methods named “connect”, the class they belong to, along with the github repo that contains them?

![3-4](https://cloud.githubusercontent.com/assets/11991105/20261043/c8719cdc-aa64-11e6-800a-f47dd991f5aa.png)

This query took 31286 ms (as opposed to 12380) to execute and returned 12380 rows, which means that it executed in approx half the time that it did in the without-index version.

