# Data Modelling Topologies of a Graph Database

_Captured: 2017-03-03 at 19:25 from [dzone.com](https://dzone.com/articles/data-modelling-topologies-of-a-graph-database?edition=273883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-03)_

![Image title](https://dzone.com/storage/temp/4478941-network-topology.jpg)

## Definition

There is a lot of confusion with the **definition of graph databases**. In my opinion, any definition that avoids any reference to the semantics of nodes and edges or their internal structure is preferable. Failing to follow this guideline, it is unavoidable to favor specific implementations, e.g. [Property Graph Databases](http://neo4j.com/developer/graph-database/) or [Triple Stores](http://en.wikipedia.org/wiki/Triplestore), and you may easily become myopic to other types that are based on different models, e.g. [hypergraph databases](http://hypergraphdb.org/), or different data storage paradigms, e.g. [key-value stores](http://en.wikipedia.org/wiki/Key-value_database). Therefore, I propose we adopt a vendor neutral definition, such as the following one, which cannot exclude any future type of graph database.

  1. > A Graph Database is a database that uses a graph topology, i.e. vertices and edges, to manage information at the conceptual level independent of the logical and physical implementation of the graph data structure. -- _** Athanassios I. Hatzis, 28th February 2017**_

## Graph Databases Per Data Model

That said, there are many differences in the conceptual, logical, and physical layers of graph databases. These affect everything -- visualization, query language, indexing, scaling, and transactions. Now, let me focus on the conceptual/logical layer, where my work is based. Depending on the structure of nodes and edges, one can describe the following three different data models.

  * **Property Graph Data Model**

    * Entity-centric with embedded properties and edges with **bidirectional linking **-- Directed Labeled Graphs

    * Neo4J, OrientDB, ArrangoDB, etc.

  * **Triple/Quadruple Data Model**
    * Edge-centric with **unidirectional linking** on vertices -- Directed Labeled Graphs
    * GraphDB, AllegroGraph, OpenLink Virtuoso, etc.
  * **Associative Data Model**
    * Hypernodes, Hyperedges, **bidirectional linking --** Hypergraph/Bipartite Graph
    * Topic Map Data Model, R3DM/S3DM, X10SYS (AtomicDB), HypergraphDB, Qlik Technology

There are two main differences between **(1)** and **(2)**. First, the type of edges in a property graph, by definition, is bidirectional. You can traverse any edge both ways, despite the fact there is a direction on the edge. On the contrary, with RDF, you have to define two labeled edges with opposite directions to achieve bidirectional linking. And secondly, in literal triples, object parts are properties of a subject part, but they are **not **first-class citizens and they are **not** embedded inside the structure of Entity nodes of a property graph.

I left the associative data model as the last thing to mention. R3DM/S3DM is the reincarnation of [Topic Maps](https://en.wikipedia.org/wiki/Topic_Maps), the de facto standard for the representation of associations. The following series of posts on associative data modeling is written with a hands-on practice style. It is an attempt to clear the information glut of many-to-many relationships (a.k.a associations) with a thorough examination of well-known data models and at the same time introduce R3DM/S3DM to the public.

## Epilogue

The verdict from this quick review on graph databases is that I have reasons to believe that associative data modeling is far more powerful and expressive than the other two. I foresee that DBMS vendors that will incorporate in their products R3DM/S3DM technology will eventually have a significant competitive advantage.
