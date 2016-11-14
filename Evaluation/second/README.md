###Second Experiment - (Added Indexes)

According to second experiment, we added some indexes in our distributed database in order to speed up our queries:

![2-1](https://cloud.githubusercontent.com/assets/11991105/20259972/31c59cba-aa60-11e6-933e-7d3ba4acb3f4.png)

We have added the following indexes (as shown in the screenshots above):
 - Method(:repoURL)
 - Method(:name)
 - Class(:name)
 - Class(:repoURL)
 - Repo(repoURL) -- this one is also a unique constraint

We will now issue the same queries again (*Note that we've restarted the server, so our page cache was empty by the time we started this experiment):

1 Give me all the methods declared on the Repository xxx?

![2-2](https://cloud.githubusercontent.com/assets/11991105/20260098/cc942bbc-aa60-11e6-8836-e1eea242ab1f.png)

We ‘ve noticed a huge acceleration on our query, as this time the query took 2810 ms to execute, and it returned 3385 rows. This was the effect of the index present on the Method(:repoURL)

2 Give me all the parameters of the method xxx?

![2-3](https://cloud.githubusercontent.com/assets/11991105/20260149/0c7a6ba6-aa61-11e6-8d83-97b6f256c278.png)

Again, we notice a huge improvement. This query took just 74 ms to execute, to return 1 row.

3 Give me all the methods named “connect”, the class they belong to, along with the github repo that contains them?

![2-4](https://cloud.githubusercontent.com/assets/11991105/20260248/727eb9f2-aa61-11e6-8502-5e23326214ce.png)

This query took 12380 ms to execute and returned 12380 rows, which means that it executed in approx half the time that it did in the without-index version. 

Highlighting some important observations:
 - Indexes on the parameters that are asked (via WHERE clauses or as property attributes like { name=”methodName”}) have a huge impact on the performance, with the overhead of a few more GB.
 - When we fetch a node, its closely related ones (e.g the methods of a class, the parameters of a method), are fetched into the cache with them so the query gets a significant boost.


