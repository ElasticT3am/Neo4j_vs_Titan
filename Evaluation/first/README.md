###First Experiment

According to the [neo4j memory configuration guidelines](https://neo4j.com/developer/kb/how-to-estimate-initial-memory-configuration/) we've configured our server as follows:

* Java Heap Size: 6 GB
* Page Cache Memory: 16 GB

We'll’ present different kind of queries, each one targeting specific portions of the graph

1  “How many repositories - JavaLines of code have we indexed?”

![1](https://cloud.githubusercontent.com/assets/11991105/20217879/af4f61bc-a82a-11e6-8a3f-33fd9f14a2f0.png)

This query took 10904 ms to execute. It touched 66456 nodes (that correspond to the repositories), and then asked for the LinesOfJavaCode property of each node. If we issue this query again, we ‘d expect to see the result of the page cache:

![2](https://cloud.githubusercontent.com/assets/11991105/20217978/1cf1e3fc-a82b-11e6-88e7-a2cc2ead3d83.png)

Indeed, we got our result back  in just 162 ms.

2  “Give me all the methods declared on the Repository xxx?”

![3](https://cloud.githubusercontent.com/assets/11991105/20217995/321b031c-a82b-11e6-8609-0a8e30d4f622.png)

This query took 37203 ms to execute, and it returned 3385 rows. It looked through the method nodes (28.314.628 in total) to check weather the repoURL matches the expected (we don’t have any index on this property yet), and then returned the method names. Note that this query touches a large portion of the graph, so we don’t observe the effect of the page cache here if we issue this query again. 

3  “Give me all the parameters of the method xxx?”

Let’s now ask for the parameters of one of the methods we got from the previous query. This would be an expensive operation in a relational database (it would need joins), but it neo4j it takes pretty much the same time as the previous one, because related nodes are put close in the disk

![4](https://cloud.githubusercontent.com/assets/11991105/20218103/92ce281a-a82b-11e6-9ee6-9d9c957a2426.png)

This query took 24174 ms to execute, to return 1 row. Again, we needed to look up every method node to find the one with repoURL=... and method.name=... (we have no indexes yet) , that’s why the query took so long. 

4  “Give me all the methods named “connect”, the class they belong to, along with the github repo that contains them?”

![5](https://cloud.githubusercontent.com/assets/11991105/20218151/cd174e3e-a82b-11e6-8b5c-d373c07b1ecc.png)

This query took 24022 ms to execute and returned 12380 rows. Again, we needed to look up every method node to find the methods named “connect”, and then look up their relationships to get class name, and fetch the property repoURL. They “heavy part” of the query would be again to check the method name, that checks a large portion of our graph.
