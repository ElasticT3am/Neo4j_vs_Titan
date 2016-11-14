#Neo4j Evaluation

##Testbed

Elastic TEAM created a neo4j cluster consisting of 3 nodes (master - slave - arbiter).

The neo4j master node lies on a physical machine with the following specs:
* Intel Core I5 CPU , 4 cores
* 24 GB RAM (DDR3)
* 120 GB Solid State Drive
* OS: Linux Mint 17


The raw content that corresponds to the repositories downloaded from github was approximately 10 Terra Bytes. We did not have that much capacity available, so we decided to delete the raw github content after processing - uploading to neo4j. We ‘ve introduced some command-line-parameters (see our  project for more info), in order for this behavior to be configurable (--no-keep-files option). More information about Elastic TEAM's project github-repo-parser, can be found [here](https://github.com/ElasticThree/Neo4j_vs_Titan.git)

####Our neo4j database consists of the following:

Java lines of Code - 544.477.667  
Github repositories - 66.456  
Total neo4j nodes - 74.837.377
Total relationships - 69.995.580
Properties - 149.108.239
Db index size in total - 39.54  (GiB) 



###[First Experiment](https://github.com/ElasticThree/Neo4j_vs_Titan/tree/master/Evaluation/first)

###[Second Experiment](https://github.com/ElasticThree/Neo4j_vs_Titan/tree/master/Evaluation/second)

###[Third Experiment](https://github.com/ElasticThree/Neo4j_vs_Titan/tree/master/Evaluation/third)
