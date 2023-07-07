# Cheatsheet: Chapter 1 - Reliable, Scalable and Maintainable Applications of Designing Data-Intensive Applications

This chapter introduces the concept of data-intensive applications and focuses on their building blocks, design principles, and handling faults. As a software engineer, understanding these concepts is crucial for designing and building robust applications that can handle large amounts of data efficiently and reliably.

## A. Understanding Data-Intensive Applications

1. **Data-Intensive vs. Compute-Intensive**:
   - Data-intensive applications are constrained more by data volume, complexity, and change rate than by computational capacity.

## B. Standard Building Blocks for Data-Intensive Applications

1. **Databases**: Store data reliably.
2. **Caches**: Speed up data retrieval by caching results.
3. **Search Indexes**: Efficiently allow data searching/filtering.
4. **Stream Processing**: Asynchronously send messages between processes.
5. **Batch Processing**: Scheduled large-scale data processing.

6. **Blurring Boundaries in Data Tools**:
   - Modern tools do not fit neatly into traditional categories (e.g., Redis can be used as a message queue, Apache Kafka as a durable message queue).
   - Combining different tools requires ensuring data remains consistent and system performance is maintained.

## C. Design Principles

1. **Reliability**:
   - Ensure correct functionality and performance even in adverse conditions.
   - Tolerate user mistakes and unexpected usage.
   - Protect against unauthorized access.
   - Implement fault tolerance through hardware redundancy and software designs.
   - Performance should suffice for the use case, expected load, and data volume.

2. **Scalability**:
   - Capacity to handle increased data volume, traffic, or complexity.
   - Understanding and describing the load and performance characteristics.
   - Scaling strategies can include scaling up (more powerful machine) or scaling out (more machines).

3. **Maintainability**:
   - Enable efficient work on the system over time.
   - Different engineers should be able to work on the system productively.
   - Simplify routine tasks and reduce complexity.
   - Employ loosely coupled modules.

## D. Handling Faults

1. **Hardware Faults**:
   - Use redundancy (e.g., RAID for disks, dual power supplies) and fault-tolerance designs to reduce system failure due to hardware faults.

2. **Software Faults**:
   - Monitor and correct systematic errors. Software fault-tolerance gains importance in large-scale applications and cloud platforms.

3. **Human Errors**:
   - Minimize opportunities for error through good design and allow easy recovery.

4. **Intentionally Inducing Faults**:
   - Like Netflix’s Chaos Monkey, intentionally inducing faults to test fault-tolerance mechanisms.

## E. Performance and Scalability

1. **Throughput and Response Time**: Important metrics for performance evaluation.
2. **Latency vs. Response Time**: Latency is the waiting time, whereas response time includes processing, network delays, and queueing.
3. **Response Time Distribution**: Consider percentiles (p50, p95, p99) instead of averages for user experience.
4. **Stateless vs. Stateful Services**: Stateless services are easier to distribute and scale.

## F. Practical Considerations

1. **Adaptive System Design**: Optimize for common use cases and be flexible to changes.
2. **No One-Size-Fits-All**: Architecture should be application-specific and built around load parameters.
3. **Building Blocks and Patterns**: Use general-purpose building blocks in familiar patterns for scalable architectures.
4. **Human Error Mitigation**: Design error-resistant interfaces, provide training, implement quick rollback procedures.
5. **Load Testing**: Understand system limitations through load testing with relevant parameters.

## G. Summary

This chapter sets the stage for the rest of the book, which dives deeper into the principles and practicalities of data systems. As an application developer, you should embrace your role as a data system designer when developing data-intensive applications, keeping in mind the three key pillars: reliability, scalability, and maintainability. Staying updated with the latest tools and trends in data-intensive applications is essential as environments and requirements continually change.

## H. Practical Application for Software Engineers

- Be comfortable with different data tools and understand their primary functions and potential unconventional uses.
- Practice inducing faults in your applications to identify weaknesses and improve fault tolerance.
- Consider using hardware redundancy and software fault-tolerance techniques to increase system reliability.
- Stay updated with the latest tools and trends in data-intensive applications.

# Cheatsheet: Chapter 2 - Data Models and Query Languages of Designing Data-Intensive Applications

## A. Data Models

### 1. Importance and Options
- Data models shape how you conceptualize problems and write software.
- Familiarize yourself with the relational model, document model, and graph-based models.
- Applications are often built by layering one data model over another.

### 2. Object-Relational Mismatch
- Be aware of the impedance mismatch between object-oriented programming and relational databases.

### 3. Relational Model
- Data is organized into tables, each table being an unordered collection of tuples (rows).
- Normalize data to store information in one place and refer to it using identifiers to avoid duplication and inconsistencies.
- Many-to-one and many-to-many relationships are essential in representing complex data, and relational databases handle them well.

### 4. Document Model
- Data is represented in formats like JSON or XML documents.
- Document model provides schema flexibility, enabling more agile and evolving data structures.
- Related data can be stored together within the same document, benefiting performance when the entire document is often needed.
- Document databases usually do not fit many-to-many relationships well and have weaker support for joins compared to relational databases.
- Use Cases: Prefer document databases for simple, less interconnected data or when schema evolution is crucial.

### 5. Graph Data Model
- Represents data as vertices (nodes) and edges (relationships).
- Vertices and edges can have properties in key-value pairs.
- Suitable for handling complex many-to-many relationships and highly connected data.
- Examples: Social networks, transport networks.

### 6. Property Graph Model
- A variant of the graph data model.
- Each vertex and edge can hold a set of key-value pairs called properties.
- Implemented by databases like Neo4j.

### 7. Triple-Store Model
- Stores data in triples of (subject, predicate, object).
- Similar to the property graph model but used in semantic web contexts.
- Subject and object are equivalent to vertices, and predicate represents a key of a property or an edge label.

### 8. Hybrid Approaches
- The lines between relational and document databases are blurring, and hybrid models are emerging.
- Use hybrid approaches to exploit the strengths of both relational and document models.

## B. Query Languages

### 1. Declarative (e.g., SQL)
- Specify the pattern of data desired without detailing how to achieve it. More concise and easier to work with.

### 2. Imperative
- Specifies operations in a sequence to achieve a goal.

### 3. MapReduce
- Neither declarative nor imperative but in-between. Good for processing large amounts of data across multiple machines.
  
### 4. Cypher (For Graph Databases)
- Declarative query language for property graphs, primarily used in Neo4j.
- Expressive for querying relationships.

### 5. SPARQL (For RDF Data Stores)
- Stands for SPARQL Protocol and RDF Query Language.
- Query language for triple-stores using the RDF data model.
- Suitable for semantic web applications.

### 6. Datalog
- Declarative logic programming language.
- Rules-based, defines new predicates based on data or other rules.
- Powerful for complex queries due to combinability and reusability of rules.

### 7. MapReduce (MongoDB)
- Processes and generates aggregate data sets.
- Map function emits key-value pairs for each document.
- Reduce function takes values with the same key and reduces them to a single value.
- Must be pure functions (no side effects).
- An alternative in MongoDB is the aggregation pipeline.

## C. Practical Application for Software Engineers

- **Choose the Data Model Wisely**: Consider relationships between data items and schema flexibility.
- **Normalize Data in Relational Databases**: But consider controlled denormalization for performance-critical scenarios.
- **Handle Relationships in Document Databases**: Be prepared to handle relationships in your application code if using document databases.
- **Optimize Data Locality**: If your application frequently accesses related data.
- **Gain Proficiency in Query Languages**: Know the query languages relevant to the data models you work with.
- **Be Open to Hybrid Approaches**: Keep abreast of evolving data models and database systems.
- **Evaluate Maintenance and Flexibility**: Consider the maintenance overhead and long-term flexibility of the chosen data model.

# Cheatsheet: Chapter 3 - Storage and Retrieval of Designing Data-Intensive Applications

## A. Key Concepts

### 1. **Storage Engines**:
- Storage engines dictate how databases store and retrieve data.
- Understanding storage engines is crucial for selecting the right database and tuning performance.

### 2. **Data Structures in Databases**:
- Log-Structured and B-tree are common data structures used in storage engines.
- Log-Structured storage appends data to a file, while B-trees keep key-value pairs sorted by key.

### 3. **Log-Structured Storage**:
- **Append-only logs**: Efficient for writes but requires indexes for efficient reads.
- **Segmentation and Compaction**: Breaks logs into segments and periodically removes obsolete data.
- **SSTables and LSM-Trees**: Combines sorted segments (SSTables) with in-memory balanced trees (memtables) for efficient writes and range queries.

### 4. **B-Trees**:
- **Widely used**: B-trees are standard for most relational and many non-relational databases.
- **Sorting and Indexing**: Keeps data sorted by key and maintains an index for efficient lookups and range queries.
- **Write-Ahead Log (WAL)**: Logs every modification before it’s applied to the B-tree for crash recovery.
- **Optimizations**: Such as copy-on-write, abbreviating keys, sequential layout, and additional pointers can improve performance.

### 5. **Hash Indexes**:
- Use an in-memory hash map to keep track of the offset in the data file for each key.
- Efficient for workloads with frequent updates but requires all keys to fit in memory.

### 6. **Secondary Indexes**:
- Essential for efficient joins and can be constructed from key-value indexes.
- Can use either B-trees or log-structured indexes.

### 7. **Multi-column and Fuzzy Indexes**:
- **Multi-column indexes**: Combine several fields into one key for complex queries.
- **Fuzzy Indexes**: Useful for searching similar keys or performing linguistic analysis (e.g., Lucene).

### 8. **In-memory Databases**:
- Store the entire dataset in memory for faster access.
- Can still be durable with logs, snapshots, or replication.

### 9. **Non-Volatile Memory (NVM)**:
- Evolving technology that may impact future database and storage engine choices.

### 10. **OLTP vs. OLAP**:
- OLTP (Online Transaction Processing) is optimized for high volumes of small read/write transactions.
- OLAP (Online Analytical Processing) is optimized for complex analytical queries over large datasets.

### 11. **Data Warehousing**:
- A specialized database optimized for analytics, usually with a separate schema and storage engine from OLTP systems.
- Consider using a data warehouse to offload analytics workload from transactional systems.

### 12. **Schemas for Analytics: Stars and Snowflakes**:
- Star Schema: A fact table surrounded by dimension tables.
- Snowflake Schema: Similar to Star Schema but with dimensions further normalized into sub-dimensions.

### 13. **Column-Oriented Storage**:
- Stores each column of data separately, facilitating better compression and faster query performance for analytical workloads.

### 14. **Materialized Aggregates**:
- Precompute and cache the results of aggregate queries in materialized views or data cubes for performance optimization.

### 15. **Divergence Between OLTP Databases and Data Warehouses**:
- OLTP databases and data warehouses are optimized for different query patterns, even though they might both offer SQL query interfaces.

### 16. **Vectorized Processing**:
- A technique for optimizing CPU cycle usage by operating on compressed column data in chunks.

### 17. **Sort Order in Column Storage**:
- Sorting rows in column storage creates long sequences of repeated values, helping in compression and optimizing queries targeting ranges/groups.

### 18. **Performance Trade-Offs**:
- Indexes speed up reads but can slow down writes. The choice and optimization should be based on the application's query patterns.

## B. Practical Application for Software Engineers

1. **Select the Appropriate Database and Storage Engine**: Choose a database system and storage engine that aligns with your application's primary needs (OLTP or OLAP).

2. **Design Efficient Schemas**: Use star or snowflake schemas for analytics. Be aware of trade-offs between normalization and query performance.

3. **Optimize Data Structures and Indexes**: Understand and optimize the data structures and indexes according to the query patterns and storage engine.

4. **Balance Performance Trade-Offs**: Be conscious of the trade-offs between optimizing for writes and reads.

5. **Use Materialized Aggregates for Analytics**: Implement materialized views or data cubes for faster query performance in analytical workloads.

6. **Keep Abreast with Technology**: Monitor emerging storage technologies such as NVM, and assess their applicability.

7. **Evaluate In-memory Options**: Evaluate the feasibility and benefits of in-memory databases for performance-critical applications.

8. **Efficient ETL Processes**: Plan and optimize the Extract, Transform, Load (ETL) processes effectively for data migration.

9. **Tuning for Performance**: Knowing storage internals is invaluable for performance tuning, schema design, and informed architectural decisions.

10. **Scalability and Performance Considerations**: Ensure that the database and storage mechanisms are scalable and performant for your specific use case.

11. **Be Prepared for Recovery**: Implement mechanisms like Write-Ahead Log (WAL) or snapshots to protect against data loss and ensure quick recovery in case of crashes.

# Cheatsheet: Chapter 4 - Encoding and Evolution of Designing Data-Intensive Applications

## A. Key Concepts

### 1. Evolvability and Schema Changes:
- Applications evolve over time, and systems must be built to adapt to changes, including modifying data storage for new fields or records.

### 2. Backward and Forward Compatibility:
- Backward compatibility: newer code can read data written by older code.
- Forward compatibility: older code can read data written by newer code. It's harder to achieve than backward compatibility.

### 3. Formats for Encoding Data:
- Encoding translates in-memory representation (objects, structs) to a byte sequence (serialization), while decoding is the reverse process (deserialization).

### 4. Encoding Formats:
- Language-Specific: Convenient but tied to a specific language, may have security vulnerabilities, often inefficient, and not great for compatibility.
- JSON, XML, CSV: Language-independent but have issues with ambiguity, optional schema support, and lack of binary strings support.
- Binary Encoding Formats (MessagePack, Avro, Thrift, Protocol Buffers): More compact and efficient, often used with a schema.

### 5. Schema Evolution:
- Enables flexibility, ensures compatibility, and allows different parts of the system to evolve independently.

### 6. Dataflow:
- Data flows between processes via databases, service calls (REST and RPC), and asynchronous message passing including the use of message brokers like RabbitMQ, ActiveMQ, Apache Kafka, etc.
- Message-Passing Communication is usually one-way and asynchronous.
- Message brokers ensure messages are delivered to one or more consumers or subscribers and are used for decoupling, buffering, and ensuring message delivery even in the event of recipient unavailability.

### 7. Distributed Actor Frameworks:
- Extend the actor model for scaling across multiple nodes.
- Encapsulate logic in actors with local state, communicating via asynchronous messages.
- Transparently encodes messages for network communication.
- Examples include Akka, Orleans, and Erlang OTP.
- Attention to message encoding and schema changes for backward/forward compatibility is essential.

### 8. Modes of Dataflow:
- Databases: writer encodes data and reader decodes it.
- RPC and REST APIs: client encodes a request, the server decodes the request and encodes a response, the client decodes the response.
- Asynchronous message passing: nodes communicate by sending encoded messages, decoded by the recipient.

## B. Practical Application for Software Engineers:

### 1. Think Ahead:
- Consider future evolvability and schema changes when designing data storage and schema. Plan for forward and backward compatibility.

### 2. Choose Encoding Format Wisely:
- Choose the right encoding format by considering compatibility, efficiency, and language constraints.

### 3. Use Schemas:
- Use explicit schemas, especially in binary encoding formats, for documentation and avoiding ambiguities.

### 4. Be Cautious with Language-Specific Formats:
- Avoid language-specific serialization for long-term storage.

### 5. Test Compatibility:
- Regularly test backward and forward compatibility.

### 6. Handle Schema Evolution:
- Assume that the schema will change, plan for it, and make prudent use of required and optional fields.

### 7. Keep Data Transformations Simple:
- Prefer simple, additive changes to data formats and avoid complex transformations.

### 8. Be Mindful of Security:
- Avoid formats that can instantiate arbitrary classes or execute code upon decoding.

### 9. Understand Trade-offs:
- Know the trade-offs of different encoding formats and choose wisely based on the use case.

### 10. Handle Large Numbers and Nulls Carefully:
- Be cautious with languages that don't handle large numbers well, and use union types to handle nulls where necessary.

### 11. Document and Communicate:
- Ensure schema changes are well-documented and communicated to stakeholders.

### 12. Use Code Generation Tools:
- Utilize tools provided by encoding formats like Thrift, Protocol Buffers, and Avro to produce classes in various languages.

### 13. Handle Writer’s and Reader's Schemas:
- Understand the importance of writer's and reader's schemas in Avro and ensure their availability during data decoding.

### 14. Microservices and Service APIs:
- Design services to be independently deployable and evolve without breaking compatibility. Ensure data encoding is compatible across versions in service APIs.

### 15. Archival Storage:
- Encode database snapshots or backups using the latest schema and consider column-oriented formats for analytics.

### 16. Key Advice for Evolvability:
- Choose data encodings and communication methods that support backward/forward compatibility. This ensures easier application evolution, frequent deployments, and no downtime during upgrades.

# Cheatsheet: Key Takeaways from Part II of Designing Data Intensive Applications

## A. Distributed Data Overview
   - Distributing data across multiple machines can be essential for scalability, fault tolerance/high availability, and reducing latency.
   
## B. Reasons for Distributing Data
   - **Scalability**: Distribute data to handle a larger volume of data, read or write loads that single machines cannot handle.
   - **Fault tolerance/high availability**: Use multiple machines to provide redundancy; if one fails, others can take over.
   - **Latency**: Locate servers close to users globally to reduce data travel time and improve performance.

## C. Approaches to Scaling
   - **Vertical Scaling (Scaling Up)**: Increase the power of a single machine (CPUs, RAM, disk capacity). Limitations include higher cost and limited fault tolerance.
   - **Shared-Disk Architecture**: Uses several machines with independent CPUs and RAM, but the data is stored on an array of shared disks. This approach has limitations due to contention and overhead of locking.
   - **Shared-Nothing Architecture (Horizontal Scaling or Scaling Out)**: Each machine (node) operates independently, using its CPUs, RAM, and disks. Coordination between nodes is achieved at the software level.
   
## D. Shared-Nothing Architecture
   - This approach doesn't require special hardware and is well-suited for cloud deployments and distributing data across multiple geographic regions.
   - Although powerful, it adds complexity and can sometimes limit data model expressiveness.
   
## E. Techniques for Distributing Data
   - **Replication**: Keep copies of the same data on different nodes, potentially in different locations. This adds redundancy and can improve performance.
   - **Partitioning (Sharding)**: Split a large database into smaller subsets called partitions, which can be assigned to different nodes.
   - Replication and partitioning are separate but often used together.

## F. Considerations in Distributed Systems
   - Developers need to be aware of the constraints and trade-offs in distributed systems.
   - Distributed shared-nothing architecture often requires careful planning and considerations for application complexity.
   - Distributed systems involve difficult trade-offs and understanding transactions and potential issues is critical.

## G. What to Expect Next
   - The book will discuss transactions to understand the various issues in data systems.
   - It will also discuss the fundamental limitations of distributed systems.
   - Part III will address how to integrate several datastores into a larger system to satisfy complex application needs.

## H. Practical Application for Software Engineers:
   - Consider the data demands of your application and choose between vertical scaling and shared-nothing architecture based on cost, complexity, and future scalability.
   - Use replication and partitioning techniques to distribute data across multiple nodes for improved performance and redundancy.
   - Be aware of the complexity added by distributed systems and make informed trade-offs.
   - Continuously reassess the scalability and fault tolerance of your application as it evolves and grows.

# Cheatsheet: Chapter 5 - Replication of Designing Data-Intensive Applications

## A. Introduction
- Replication is keeping a copy of the same data on multiple machines connected via a network.
- It's used to reduce latency, increase availability, and improve read throughput.

## B. Why Replicate Data?
1. Reduce latency by keeping data geographically closer to users.
2. Increase availability by allowing the system to continue working even if some parts fail.
3. Increase read throughput by scaling out the number of machines that can serve read queries.

## C. Challenges in Replication
- Handling changes in replicated data is challenging.
- Replication lag and eventual consistency issues.
- Handling leader failure in leader-based replication.
- Managing cross-device consistency and read-after-write consistency.

## D. Replication Strategies

### 1 Single-leader Replication
- One replica is designated as the leader. Writes must be sent to the leader. The other replicas are followers.

### 2 Multi-leader Replication
- More than one replica can accept write requests.
- Allows for writes in multiple data centers, increasing fault-tolerance.
- Requires mechanisms for handling conflicts due to concurrent writes.
- In multi-leader configuration, the order of writes isn't well defined. Replicas must converge towards a consistent state.
- Multi-leader replication tools often support custom conflict resolution logic embedded in the application code.

#### 2.1 Multi-leader Replication Topologies
1. **All-to-All**: Every leader sends its writes to every other leader.
2. **Circular**: A single flow of data changes as each node receives and forwards writes.
3. **Star Topology**: One root node forwards writes to all other nodes.

- More densely connected topologies are more fault-tolerant but might lead to network congestion or out-of-order arrival of writes.

### 3 Leaderless Replication
- Writes are sent to multiple replicas, and there's no designated leader.
- The system can continue processing writes even when a node is down.
- Quorum-based reads and writes can detect and handle stale data.
- Replication strategies such as read repair and anti-entropy processes help maintain consistency across replicas.
- Sloppy quorums improve availability during network partitions, at the cost of potentially reading stale data.
- Hinted handoff helps maintain durability of writes during network partitions.

## E. Synchronous vs. Asynchronous Replication
- **Synchronous Replication**: Leader waits until at least one follower has written the data.
- **Asynchronous Replication**: Leader sends the data and doesn’t wait for followers.
- **Semi-synchronous Replication**: A hybrid approach, usually with one follower being synchronous and others asynchronous.

## F. Handling Failures
- **Follower Failure**: Each follower keeps a log of data changes it received from the leader. It recovers by applying data changes from its log.
- **Leader Failure (Failover)**: A follower must be promoted to be the new leader.

## G. Replication Logs Implementation
1. **Statement-Based Replication**: The leader logs every write request and sends them to followers.
2. **Write-Ahead Log (WAL) Shipping**: The leader sends its write-ahead logs to followers.
3. **Trigger-Based Replication**: Using triggers to log changes to a separate table that an external process can read and replicate to another system.

## H. Conflict Resolution Strategies
1. **Last Write Wins (LWW)**: Uses unique IDs for each write (timestamps, UUIDs, etc.), and the write with the highest ID wins.
2. **Dependent on Replica ID**: Conflictsare resolved in favor of the write from the higher-numbered replica.
3. **Merging**: Deterministically merges conflicting values.
4. **Explicit Conflict Recording**: Detects and records conflicts for later resolution by application code.

## I. Custom Conflict Resolution Logic
1. This logic can be invoked either upon writing (when conflict is detected) or upon reading (resolve and write back the result on next read).

## J. Automatic Conflict Resolution
1. **CRDTs (Conflict-free Replicated Data Types)**: Data structures that automatically resolve conflicts sensibly upon concurrent editing.
2. **Mergeable Persistent Data Structures**: Tracks history explicitly and uses three-way merge functions to resolve conflicts.
3. **Operational Transformation**: Algorithm used in collaborative editing applications to resolve conflicts during real-time editing.

## K. Read-After-Write Consistency
- Ensuring users see the data they have just written.
- Possible solutions:
  - Read user-modifiable data from the leader and other data from followers.
  - Track the time of the last update and temporarily read from the leader after an update.
  - The client remembers the timestamp of its recent write; the system ensures the replica serving the reads is up-to-date.

## L. Monotonic Reads
- Ensuring a user does not read outdated data after having seen newer data.
- Solutions include always reading from the same replica or ensuring that replicas accessed by a user are synchronized to a point in time.

## M. Implications for Software Engineers
1. Choose the appropriate replication strategy based on application requirements.
2. Synchronous replication for critical data consistency, asynchronous for performance-sensitive applications.
3. Be aware of challenges during failover and handle them diligently.
4. Implement mechanisms for read-after-write consistency.
5. Monitor system health and have alerts for timely intervention in case of failures.
6. Keep an eye on the latest research and available tools for replication to potentially incorporate better solutions as they become available.
7. Be mindful of replication lag and eventual consistency and design your application accordingly.
8. Consider manual intervention in critical failover scenarios to avoid data corruption or loss.
9. In geographically distributed systems, asynchronous replication is often more practical.
10. In multi-datacenter setups, think about how you will handle routing to maintain consistency across devices.
11. Maintain monotonic reads by ensuring that a user does not read outdated data after having seen newer data.

## N. Real-world Applications and Tools
- Databases like PostgreSQL, MySQL, and MongoDB employ replication strategies.
- Distributed message brokers like Kafka and RabbitMQ.
- Chain Replication is used in some systems like Microsoft Azure Storage.
- Tools for Trigger-Based Replication: Databus for Oracle, Bucardo for Postgres.

This is a comprehensive summary of the concepts and strategies involved in data replication, which is a critical component in designing data-intensive applications. It serves as a reference guide for software engineers to understand and apply replication concepts effectively in their work.

# Cheatsheet: Chapter 6 - Partitioning of Designing Data-Intensive Applications

## A. What is Partitioning?
- Partitioning, or sharding, involves breaking data into smaller chunks (partitions) and distributing them across multiple nodes in a database.
- Each record belongs to exactly one partition.
- A crucial technique for scalability as it enables the distribution of data and query load over multiple machines.
- Often combined with replication to enhance fault tolerance and data availability.

## B. Key Terminologies:
- **Partition/Shard**: A subset of the database's data.
- **Skew**: An imbalance where some partitions have more data or queries than others.
- **Hot Spot**: A partition with a disproportionately high load.
- **Rebalancing**: The process of moving data among nodes to maintain even distribution, especially when new nodes are added or existing nodes are removed.

## C. Partitioning Strategies:
1. **Partitioning by Key Range**:
   - Assigns a continuous range of keys to each partition.
   - Pros: Efficient for range scans.
   - Cons: May lead to hot spots if the range is not distributed properly.
   
2. **Partitioning by Hash of Key**:
   - Uses a hash function on keys to distribute data uniformly across partitions.
   - Pros: Good for evenly distributing write load.
   - Cons: Makes range queries inefficient.
   
3. **Directory-based Partitioning**:
   - Maintains a directory of metadata to track which partition contains which set of keys.
   - Pros: Flexibility in partitioning; partitions can be of different sizes and can be relocated.
   - Cons: Directory can become a bottleneck or point of failure.

4. **Partitioning Secondary Indexes by Document (Local Index)**:
   - Each partition maintains its secondary indexes, covering only the documents in that partition.
   - Pros: Simplifies writes.
   - Cons: Makes reads more expensive (scatter/gather).
   
5. **Partitioning Secondary Indexes by Term (Global Index)**:
   - Constructs a global index covering data in all partitions.
   - Pros: More efficient reads.
   - Cons: Slower, more complicated writes.

6. **Dynamic Partitioning**:
   - Adapts the number of partitions according to the total data volume.
   - Suitable for both key-range and hash partitioning.
   
7. **Partitioning Proportional to Nodes**:
   - The number of partitions is proportional to the number of nodes.
   - Mostly relies on hash-based partitioning.

## D. Rebalancing:
- Necessary for load balancing especially when the dataset size increases or a machine fails.
- Can be automatic (system-controlled) or manual (administrator-controlled).

## E. Query Routing:
- Mechanism to route client requests to the correct node.
- Methods:
   1. **Any Node Forwarding**: Clients contact any node; the node responds directly if it owns the required partition, otherwise, it forwards the request.
   2. **Routing Tier**: Clients send requests to a routing tier that forwards them to the appropriate node.
   3. **Client-Side Partition Awareness**: Clients are aware of partitioning and directly connect to the appropriate node.

## F. Practical Tips:
1. Choose a partitioning strategy that aligns with your data access patterns.
2. Monitor partition sizes and loads for rebalancing needs.
3. Be mindful of hot spots and design keys to avoid them.
4. Understand how your database handles partitioning and query routing.
5. When combining partitioning with replication, manage consistency and fault tolerance carefully.
6. Use external coordination services (e.g., ZooKeeper) to keep track of cluster metadata.
7. Be aware of consistency challenges in secondary indexes, especially in the presence of network partitions and failures.
8. Decide between automatic and manual rebalancing based on the trade-offs. Automatic rebalancing is less labor-intensive but can be unpredictable, whereas manual rebalancing is more controlled but requires more effort.
9. Design your system to scale horizontally by adding more nodes as needed.
10. Evaluate the impact of partitioning strategies on both read and write operations, and optimize based on your application’s requirements.

This is a brief and consolidated summary of partitioning concepts and strategies, which are essential in scaling databases for large datasets and high query loads. Use it as a reference guide while designing and managing partitioned systems in your role.

# Cheatsheet: Chapter 7 - Transactions of Designing Data-Intensive Applications

## A. Key Concepts

### 1. ACID Properties
1. **Atomicity**: Transactions are all-or-nothing units; if an error occurs, changes are rolled back.
2. **Consistency**: Transactions bring the database from one valid state to another, preserving application-specific invariants.
3. **Isolation**: Transactions do not interfere with each other; ensures all or none of the writes from another transaction are visible.
4. **Durability**: Committed data is not lost even in case of failures.

### 2. Transaction Isolation Techniques
1. **Serializable Isolation**: Strongest level, transactions executed as if serial. Rarely used due to performance penalties.
2. **Snapshot Isolation**: Transactions read from a consistent snapshot of the database.
3. **Read Committed**: Basic level, prevents dirty reads and writes.
4. **Two-Phase Locking (2PL)**: Control concurrent access by acquiring locks.
5. **Serializable Snapshot Isolation (SSI)**: Provides full serializability with less performance penalty than snapshot isolation.
6. **Actual Serial Execution**: Execute transactions one at a time on a single thread.

### 3. Concurrency Control
1. Ensures that transactions maintain isolation.
2. Multi-Version Concurrency Control (MVCC) is commonly used for snapshot isolation.
3. **Lost Update Problem**: Two concurrent transactions read-modify-write a value, resulting in one of the modifications being lost.
4. **Atomic Write Operations**: Use concurrency-safe atomic operations provided by the database to avoid lost updates.
5. **Explicit Locking**: Lock objects before read-modify-write cycle.
6. **Automatically Detecting Lost Updates**: Databases like PostgreSQL can automatically detect and abort transactions with lost updates.
7. **Compare-and-set**: For databases without transactions, allow update only if value hasn’t changed since last read.
8. **Write Skew**: Generalization of lost update problem, where two transactions read the same objects and then update some of those objects.
9. **Phantom**: A write in one transaction changes the result of a search query in another transaction.
10. **Materializing Conflicts**: Turning a phantom into a lock conflict by introducing a lock object in the database.
11. **Deadlocks**: Occur when transactions are waiting for each other to release locks. The database usually detects and resolves deadlocks by aborting one of the transactions.

### 4. Error Handling and Aborts
1. Transactions can be aborted and retried in case of errors.
2. Retrying should be handled carefully to avoid redundant operations.

### 5. Secondary Indexes
1. In databases with secondary indexes, these need to be updated along with primary data.

### 6. Durability and Replication
1. Combine multiple techniques like writing to disk, replication, backups for better durability.
2. Understand the trade-offs and risks.

### 7. Distributed Transactions
1. Transactions in distributed databases have additional challenges and considerations.

### 8. Partitioning
1. Data can be partitioned across multiple cores/nodes to allow parallel processing.
2. Transactions that only access data within a single partition can be processed in parallel.
3. Cross-partition transactions require coordination and are slower.

### 9. Encapsulating Transactions in Stored Procedures
1. Submit transactions as stored procedures to the database ahead of time.
2. Useful for actual serial execution to eliminate network communication during the transaction.

## B. Practical Application and Best Practices

1. **Evaluate Need for Transactions**: Assess if your application critically requires transactions. Use them for high reliability and consistency.
2. **Understand Database Capabilities**: Familiarize yourself with the ACID properties supported by your database and configure the transaction isolation levels according to your needs.
3. **Error Handling**: Implement proper error handling in case transactions fail. Know when to retry aborted transactions.
4. **Concurrency Control**: Be familiar with concurrency issues and use appropriate isolation levels to prevent data anomalies.
5. **Optimize Performance**: If transactions are a performance bottleneck, consider optimizing or using weaker isolation levels where acceptable.
6. **Handling Secondary Indexes**: Be cautious when dealing with secondary indexes; understand how they interact with transactions.
7. **Durability Techniques**: Combine multiple techniques for better durability and data safety. Understand the trade-offs involved.
8. **Distributed Systems**: If dealing with distributed databases, consider additional challenges and requirements for transactions.
9. **Be Cautious with Marketing Terms**: Understand the actual guarantees a system provides before relying on them, especially regarding ACID compliance.
10. **Think Holistically**: Consider the entirety of your data model, transaction handling mechanisms, and the properties and trade-offs of your databases to ensure data consistency and durability according to your application’s requirements.
11. **Use Atomic Operations**: Prefer atomic write operations where possible.
12. **Handle Lost Updates**: Understand how your database handles lost updates and choose the best method.
13. **Use Serializable Isolation**: When necessary, use serializable isolation to avoid write skew and phantoms, but consider performance implications.
14. **Use Explicit Locking Wisely**: Lock rows that a transaction depends on if serializable isolation is not feasible.
15. **Enforce Database Constraints**: Use database-level constraints to enforce integrity.
16. **Consider Partitioning for Scalability**: Utilize data partitioning for scaling transaction processing in high-throughput systems.
17. **Use Stored Procedures for Serial Execution**: Encapsulate transactions in stored procedures to reduce network communication overhead and improve execution speed.
18. **Test Concurrent Scenarios**: Include concurrency scenarios in your test cases to ensure data integrity.
19. **Stay Informed**: Keep up with best practices and new features in database management systems.

Remember that absolute guarantees do not exist, so it’s essential to understand the limitations and risks in your chosen data storage and transaction strategy. Also, always monitor and test your application under realistic workloads to validate your transaction handling strategies.

# Cheatsheet: Chapter 8 The Trouble with Distributed Systems of Designing Data-Intensive Applications

## A. Understanding Distributed Systems
- Distributed systems are complex due to factors such as network latency, hardware failures, and clock discrepancies.
- Partial failures are common in distributed systems, where some components fail while others continue to operate.
- Different nodes in a distributed system may have different views of the system state at any given time due to asynchronous communications and lack of a global clock.

## B. Network Issues in Distributed Systems
1. **Uncertainty**: It’s often unclear why a request in a distributed system doesn’t get a response - it could be due to the request or response being lost, the remote node failing, or various delays.
2. **Network Faults**: Networks are not fully reliable, and faults can occur due to misconfigurations, hardware failures, or external factors.
3. **Network Partitions (Netsplits)**: Sometimes one part of the network gets cut off from the rest due to a network fault.
4. **Handling Network Faults**: Software must handle network faults gracefully, meaning it should fail in a controlled and predictable manner.
5. **Detecting Faulty Nodes**: Detect faulty nodes to prevent sending requests to them or to elect new leaders in case of leader failure.
6. **Timeouts**: Used to deal with uncertainty, but they don't provide definite information. Choosing timeout values is a trade-off between fast detection and avoiding false positives.
7. **Cascading Failures**: Overloading a system can cause cascading failures. If under high load, transferring the load of a dead node to others may cause them to fail as well.

## C. Clocks and Timing in Distributed Systems
1. **Monotonic Clocks**: Used for measuring elapsed time between events on the same machine. They don't jump backward or forward and are suitable for measuring timeouts.
2. **Clock Synchronization and Accuracy**: Time-of-day clocks need synchronization through protocols like NTP, but perfect synchronization is practically impossible due to various factors.

## D. Communication Protocols
1. **UDP in Real-Time Communication**: UDP is suitable for real-time communication where late data is worthless.
2. **TCP vs. Circuit Switching**: TCP connections use available bandwidth dynamically, suitable for data transfers that don't have a specific bandwidth requirement.

## E. Network Utilization Strategies
1. **Synchronous vs. Asynchronous Networks**: Synchronous networks reserve a fixed amount of bandwidth (low latency, reliable), while asynchronous networks use packet-switching optimized for bursty traffic.
2. **Static vs. Dynamic Resource Partitioning**: Static resource partitioning achieves low latency but leads to underutilization. Dynamic resource partitioning maximizes utilization but may result in variable delays.
3. **Hybrid Networks**: Combines circuit-switching and packet-switching to emulate the reliability of circuit-switching while maintaining high resource utilization.

## F. Practical Recommendations for Software Engineers
1. **Acknowledge Distributed System Complexities**: Understand that distributed systems have inherent complexities such as unreliable networks, partial failures, and lack of shared memory. Take these into consideration during design and development phases.
2. **Design for Resilience**: Assume network issues and hardware failures will happen and design systems to handle these gracefully.
3. **Handle Network Partitions**: Implement mechanisms to deal with network partitions and unreliable communication.
4. **Adaptive Timeouts**: Use adaptive timeouts which adjust automatically based on observed network conditions.
5. **Optimize Garbage Collection (GC)**:
    - Minimize process pauses due to garbage collection as they affect performance.
    - Consider temporarily pausing new requests during garbage collection.
    - Periodically restart processes to prevent long-lived objects from impacting GC.
    - This is especially important in latency-sensitive systems like financial trading.
6. **Clearly Define System Models and Assumptions**: Clearly state the assumptions about system behavior (the system model), and ensure that the algorithms are designed to function correctly within the constraints of this model.
7. **Use Quorum-Based Decision Making for Reliability**:
    - Use quorums to make decisions in distributed systems. This involves collecting votes from several nodes.
    - Typically, a quorum requires an absolute majority (more than half of the nodes).
    - This approach reduces dependency on any single node and prevents conflicting decisions.
8. **Handle Leadership Carefully in Distributed Systems**:
    - Ensure there is only one leader or lock holder at a time.
    - Prevent nodes that have been declared dead or demoted from continuing to act as leaders, as this can cause inconsistencies.
9. **Byzantine Fault Tolerance (BFT)**:
    - Understand that Byzantine Fault Tolerance is necessary in systems where nodes may not follow protocol or might be malicious, such as blockchains.
    - Recognize that implementing BFT can be impractical due to complexity and cost in typical data systems.
10. **Implement Protection against Weak Faults**:
    - Employ checksums, input sanitization, and other mechanisms to guard against invalid messages due to hardware issues, software bugs, or misconfigurations.
11. **Handling Failures**: Implement fault-tolerance mechanisms and test systems under failure conditions.
12. **Recognize Clock Synchronization Challenges**:
    - Understand that clocks in distributed systems may go out of sync. This can affect algorithms that rely on time.
    - Implement strategies to handle clock synchronization issues.
13. **Monitor and Alert**: Use proper monitoring and alerting mechanisms for insights into the health of the distributed system.
14. **Cascading Failures**: Implement strategies like load shedding, rate limiting or circuit breakers to prevent cascading failures.
15. **Understand Hardware Choices**: Know the trade-offs between using specialized hardware vs. commodity machines.
16. **Clock Synchronization**: Use clock synchronization protocols but be prepared for clock drift and timestamp ambiguities.
17. **Choose Communication Protocols Wisely**: UDP for real-time applications and TCP for data transfers without specific bandwidth requirements.
18. **Optimize Network Utilization vs. Latency**: Balance between network utilization and latency based on application requirements.
19. **Consider Single Node Solutions When Possible**: If a problem can be solved using a single machine, it is often preferable due to the reduced complexity compared to distributed systems.
20. **Balance Reliability and Cost**: Understand that achieving high reliability may be costly. Evaluate the criticality of the system and make informed trade-offs between reliability and cost.
21. **Leverage Distributed Systems for Fault Tolerance and Low Latency**: Use distributed systems not just for scalability but also to achieve fault tolerance and low latency by geographically distributing data closer to users.

Remember that the challenges of distributed systems are rooted in unreliable networks, unreliable clocks, and the uncertainty of system state. Design your systems with these challenges in mind and implement strategies to handle the inherent complexities of distributed environments.