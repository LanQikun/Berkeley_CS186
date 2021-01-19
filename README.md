# SimpleDB
Database Homework of Berkeley University: Implement A Simple Database Management System 
**(You can get more details in https://sites.google.com/site/cs186fall2013/homeworks)**

The course consists of four projects that implement four core parts in the database:

**Project 1**: Implementing data management. This part is mainly to realize the management of data. Of course, it is necessary to set up the development environment and understand the overall framework of SimpleDB under the guidance. More specifically, it is necessary to implement storage, access and management of physical level data (binary files) and map it to logical level data (relational tables). At the end of this project, the most basic operation in SimpleDB, SeqScan, is also required. So after completing this project, you can scan the entire table.

**Project 2**: Implementing the operators. In this project, you will implements a series of database operators, including `insert`, `delete`, `select`, `join`, `group by`, `order by`, and so on. It is worth noting that implementing a highly efficienct version of `join` is the main and difficult question (but don't worry, you just need to learn some common algorithms, there are recommended articles at the end of this article). Plus, the `group by` and `order by` functions in SimpleDB have been simplified, so some work is actually saved. At the end of the project, we need to implement the cache management, a function that is not completed in project 1. You will learn and implement the caching mechanism, including the cache replacement algorithms (LRU, etc.).

**Project 3**: Implementing query optimization. In this project, you need to implement the cost-based optimizer. What is most difficult is to use the left-deep-tree and the idea of dynamic programming to implement the `Join` operation optimizer. Once completed, the performance of `Filter`,i.e. the SQL `where` clause, and `Join` operations will be greatly optimized.


**project 4**: Implementing transaction management. In this project, you need to implement transaction management of SimpleDB, including using 2PL protocol and NO STEAL/FORCE cache management strategy to enable ACID properties of transaction with page-level locking, and deadlock detection and abortion based on a simple timeout policy or cycle-detection in a dependency graph data structure (I implemented the latter one). Due to the use of NO STEAL/FORCE strategy, the log-based recovery, i.e. undo and redo functions, are omitted.

## Requirement of the Course

1. The projects require few knowledge of database, but in project 4, you might have to learn some concepts of transaction management through google or relevant books. Also, the references I recommend at the end of this article might help.

2. You need to know the basic grammar of Java, and it would be better if you have learned concurrency in Java (needed in Project 4). Additionally, I change Ant (which is recommended by the course) to Maven, so if you would like to run my code, you will also need to learn some basic concept in Maven (e.g. the use of POM file).

3. It takes about one month to complete the whole four projects.

What is more, when implementing the project 4, it is recommended to learn the concepts about transaction management systematically, especially ACID properties, the priority of read/write lock, 2PL protocol, etc.

## What I modified
The cache is implemented by double-ended queue, and it uses LRU page replacement algorithm.

The join of multiple tables is based on by Merge Sort.

The deadlock detection is based on resource allocation graph.

## Problems in the course original code
It dose not indicate that page number is a integer start from 0.

It only use direct path to load table files.

The catalog of database table and .dat files should be in the same directory.

It does not exchange card when cost2<cost1 in JoinOptimizer.computeCostAndCardOfSubplan.

In some tests, the table alias are missed.
