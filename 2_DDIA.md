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

## Summary

This chapter sets the stage for the rest of the book, which dives deeper into the principles and practicalities of data systems. As an application developer, you should embrace your role as a data system designer when developing data-intensive applications, keeping in mind the three key pillars: reliability, scalability, and maintainability. Staying updated with the latest tools and trends in data-intensive applications is essential as environments and requirements continually change.

## Practical Application for Software Engineers

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

## Practical Application for Software Engineers

- **Choose the Data Model Wisely**: Consider relationships between data items and schema flexibility.
- **Normalize Data in Relational Databases**: But consider controlled denormalization for performance-critical scenarios.
- **Handle Relationships in Document Databases**: Be prepared to handle relationships in your application code if using document databases.
- **Optimize Data Locality**: If your application frequently accesses related data.
- **Gain Proficiency in Query Languages**: Know the query languages relevant to the data models you work with.
- **Be Open to Hybrid Approaches**: Keep abreast of evolving data models and database systems.
- **Evaluate Maintenance and Flexibility**: Consider the maintenance overhead and long-term flexibility of the chosen data model.

# Cheatsheet: Chapter 3 - Storage and Retrieval of Designing Data-Intensive Applications

## Key Concepts

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

## Practical Application for Software Engineers

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

## Key Concepts

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

## Practical Application for Software Engineers:

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
