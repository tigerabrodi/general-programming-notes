# How Disney Hotstar Captures One Billion Emojis!

1. **Kafka for Emoji Collection**: Kafka efficiently managed the deluge of emoji reactions, acting like a high-capacity sorting system for billions of messages.

2. **Go for Concurrent Processing**: Hotstar's API servers, built with Go, handled the incoming emoji reactions. Go's concurrency capabilities, using goroutines and channels, allowed for rapid, simultaneous processing of multiple data streams.

3. **Spark for Real-Time Analytics**: Spark analyzed the emoji data in real time. Its in-memory processing and micro-batch architecture enabled the system to update viewer sentiment every two seconds, much faster than traditional methods.

4. **MQTT for Fast Messaging**: A Pub/Sub system based on MQTT protocol delivered the analyzed data to viewers with minimal delay, ensuring real-time interaction.

5. **Scalable, Resilient Architecture**: The combination of Kafka, Go, Spark, and MQTT created a scalable and resilient system that efficiently managed high traffic and reduced latency from 6 to 2 seconds.

# What Is GraphQL? REST vs. GraphQL

1. **What is GraphQL?**: Think of GraphQL as a more flexible and efficient way for clients (like web or mobile apps) to communicate with a server. Unlike traditional APIs, GraphQL lets clients specify exactly what data they need. It's like going to a buffet and being able to choose exactly what you want on your plate, rather than being served a pre-determined meal.

2. **GraphQL's Key Features**:

   - **Aggregation of Requests**: It can combine multiple data requests into a single query.
   - **Mutations**: These are GraphQL's methods for changing data (like adding or updating information).
   - **Subscriptions**: This feature allows clients to get real-time updates when data changes.

3. **Comparing GraphQL and REST**:

   - **Similarities**: Both use HTTP for requests and responses, and both can return data in JSON format.
   - **Differences**: GraphQL requests specify exactly what data and which fields are needed, whereas REST API responses are determined by the server. REST uses different URLs for different resources, while GraphQL uses a single endpoint and a schema to understand and retrieve data.

4. **Benefits of GraphQL**:

   - **Flexibility**: Clients have more control over the data they receive.
   - **Efficiency**: Reduces the need for multiple API calls (the N+1 problem in REST).

5. **Drawbacks of GraphQL**:

   - **Tooling and Complexity**: Requires specific tools and understanding for implementation, which can be an investment.
   - **Caching Challenges**: Unlike REST, which uses HTTP GET for easy caching, GraphQL's use of HTTP POST makes caching more complex.
   - **Potential for Overloading**: Clients can potentially make queries that are too demanding on the server, like causing a full table scan in a database, which can be risky.

6. **Should You Use GraphQL?**: It's all about trade-offs. GraphQL offers flexibility and efficiency, ideal for complex applications with diverse data needs. However, it requires more setup and careful management, especially for caching and preventing server overloads.

# Noisy Neighbors

1. **The Noisy Neighbor Problem**: Imagine your application is a shared apartment building. If one tenant (User A) is too loud or uses up most of the resources (like water or electricity), it affects the other tenants (User B). In your application, when User A makes a lot of requests, they consume most of the available resources (like CPU, memory), causing User B’s requests to fail due to resource shortage.

2. **Multi-Tenant Environment**: Your application is like a building with multiple tenants (users). In cloud computing, this is common where many users (tenants) share the same hardware resources.

3. **Identifying the Problem**: You notice spikes in resource usage by Tenant A, and as a result, Tenant B experiences errors. This is typical in a shared environment where one user's high demand impacts others.

4. **Solutions to the Problem**:

   - **Auto-Scaling**: This is like adding more resources (like extra water tanks or generators) when demand spikes. It automatically increases capacity to handle the load but has a delay (the trigger window).
   - **Throttling**: It’s like setting limits on how much water or electricity each tenant can use. If a tenant exceeds this limit, their resource use is restricted.
   - **Retry Mechanisms in Clients**: This is like advising tenants to try using resources again if they initially face a shortage.
   - **Load Leveling with a Queue**: Requests are lined up and processed in order, preventing overload.
   - **Restricting Operations**: In high-demand situations, limit resource-intensive activities (like searching in the app).
   - **Quality of Service Classes in Kubernetes**: Assigning different priority levels to processes. High-priority processes are less likely to be stopped when resources are scarce.
   - **Background Operations**: Schedule less critical operations for off-peak times to free up resources during high-demand periods.

5. **Final Thoughts**: The key to managing the Noisy Neighbor problem is to balance resource allocation so that all users have fair access. This involves a combination of scaling, managing demand, and prioritizing resources.

# Deep Dive into REST API

1. **Naming Conventions**:

   - Use **nouns** for endpoints, not verbs (e.g., `items`, not `createItems`).
   - Leverage logical groupings; if an object contains another, reflect this in the endpoint (e.g., `/customers/{id}/orders`).
   - Avoid exposing database structures in your API paths.
   - Use **plural nouns** for collections (e.g., `orders`) and singular for individual resources (e.g., `orders/99`).

2. **URL Structure**:

   - Keep URLs simple and avoid deeply nested structures.
   - Use hyphens (`-`) to improve readability.
   - **Version your API** to manage changes without breaking existing clients.

3. **Hypermedia as the Engine of Application State (HATEOAS)**:

   - Include navigable links in responses to guide clients through your API.
   - HATEOAS allows clients to discover resources dynamically.

4. **Filtering, Pagination, and Sorting**:

   - Implement filtering through query parameters.
   - Use pagination to manage large datasets and limit response sizes.
   - Allow sorting by fields via query parameters.

5. **Idempotency**:

   - Ensure operations like `DELETE` are idempotent; repeating them has the same effect.
   - Use HTTP status codes appropriately to reflect different outcomes of idempotent operations.

6. **Asynchronous Operations**:

   - For long-running operations, consider asynchronous processing.
   - Return a `202 Accepted` status and provide a way for clients to check operation status.

7. **Support for Partial Responses**:

   - Implement the `Accept-Ranges` header for large resources.
   - Use HTTP `HEAD` requests to fetch metadata without the full resource.

8. **Error Handling**:

   - Provide clear error messages and appropriate HTTP status codes.
   - Ensure error messages are informative for developers but don’t expose sensitive information.

9. **Security**:

   - Enforce SSL/TLS encryption.
   - Implement proper authentication and authorization.
   - Use Access Control Lists (ACLs) and rate limiting to enhance security.

10. **Documentation with OpenAPI/Swagger**:

- Use OpenAPI (formerly Swagger) for documenting your API.
- It helps in defining, visualizing, and creating interactive documentation.

# Data Structures we use every day

1. **Lists**:

   - Useful for storing ordered data.
   - Applied in task management apps (organizing tasks), social media feeds (displaying posts in order), and shopping carts.

2. **Arrays**:

   - Fixed-size, ordered collections.
   - Ideal for mathematical operations, storing data sets, and image processing (storing pixel data).

3. **Stacks** (Last-In-First-Out principle):

   - Suitable for undo/redo operations in text editors and browsing history in web browsers.

4. **Queues** (First-In-First-Out principle):

   - Manage printer jobs, user actions in games, or message handling in chat applications.

5. **Heaps**:

   - Used in task scheduling and memory management.
   - Implement priority queues for efficient access to the highest or lowest priority item.

6. **Trees**:

   - Represent data hierarchically.
   - Used in database indexing, AI decision-making, and file systems.
   - Example: Decision trees in machine learning for classification.

7. **Hash Tables**:

   - Enable efficient data lookup, insertion, and deletion.
   - Utilized in search engines, caching systems, and compilers/interpreters for symbol table management.

8. **Suffix Trees**:

   - Specialized for searching strings in documents.
   - Applied in text editors and search algorithms.

9. **Graphs**:

   - Track relationships or paths.
   - Used in social networks, recommendation engines, and pathfinding algorithms.

10. **R-trees**:

- Efficient for finding nearest neighbors.
- Crucial in mapping apps and geolocation services.

# Top 7 Ways to 10x Your API Performance

1. **Caching**:

   - Caches store results of expensive computations for quick retrieval.
   - Use Redis or Memcached to cache API responses, reducing database queries.
   - Even short-term caching can significantly boost performance.

2. **Connection Pooling**:

   - Maintains a pool of open database connections instead of opening new ones for each request.
   - Reduces the overhead of connection setups.
   - For serverless architectures, use services like AWS RDS Proxy or Azure SQL Database serverless for efficient connection management.

3. **Avoid N+1 Query Problems**:

   - Fetch related data efficiently to prevent multiple database queries.
   - For example, fetch all comments for a set of blog posts in one or two queries rather than individual queries for each post.

4. **Pagination**:

   - Breaks large data responses into smaller, manageable pages.
   - Reduces data transfer load and speeds up response times.
   - Implement using `limit` and `offset` parameters in your API.

5. **Lightweight JSON Serializers**:

   - Use fast serialization libraries to minimize the time spent converting data to JSON.
   - Efficient serialization can noticeably improve response times.

6. **Compression**:

   - Compress API responses to reduce data transfer size.
   - Modern algorithms like Brotli offer better compression ratios.
   - CDNs like Cloudflare can handle compression, offloading the task from your server.

7. **Asynchronous Logging**:
   - In high-throughput systems, logging can add latency.
   - Use asynchronous logging to quickly place log entries into an in-memory buffer, while a separate thread handles the writing to files or logging services.
   - Be aware of the potential for losing some logs in case of a crash.

# Data structures that power our databases

1. **Skip List**:

   - A probabilistic data structure for implementing sorted maps or sets.
   - Used in in-memory databases like Redis for Sorted Sets and Sorted Lists.
   - Facilitates efficient search, insertion, and deletion.

2. **Hash Index (Hash Table)**:

   - Maps keys to values using a hash function.
   - Key for fast lookups, insertions, and deletions.
   - Common in various databases, including Redis and internal mechanisms of many databases.

3. **SSTable (Sorted Strings Table)**:

   - Stores data on disk in sorted order.
   - File-based, used for large data storage in a compressed, efficient format.
   - Integral to LSM Tree architecture.

4. **LSM Tree (Log-Structured Merge-Tree)**:

   - Combines MemTable (in-memory) and SSTables (on-disk) for handling high volumes of writes.
   - Backbone of NoSQL databases like Apache Cassandra, RocksDB, and LevelDB.

5. **B-Tree and B+Tree**:

   - Balanced tree structures for efficient on-disk data storage and retrieval.
   - B+Tree stores all data in leaf nodes with internal nodes holding keys.
   - Used in databases like MySQL, Postgres, and Oracle.

6. **Inverted Index**:

   - Efficient for searching and retrieving data from large text document collections.
   - Maps words to documents, inverted from the usual document-to-word mapping.
   - Utilized in search engines like ElasticSearch.

7. **Suffix Tree**:

   - Used for efficient text searching in databases.
   - Quickly locates all occurrences of a search term within large document collections.

8. **R-Tree**:
   - Spatial index structure organizing data by geometric boundaries.
   - Facilitates fast spatial queries.
   - Employed in spatial databases like PostGIS, MongoDB, and Elasticsearch.

# Distributed Systems Patterns

1. **Ambassador Pattern**:

   - Acts as an intermediary, handling tasks like logging, monitoring, and retries for an application.
   - Example: Kubernetes using Envoy as an ambassador to simplify service communication.
   - Benefits include reduced latency and enhanced security.

2. **Circuit Breaker Pattern**:

   - Prevents cascading failures by stopping requests to a failing service, allowing it to recover.
   - Example: Netflix’s Hystrix library.
   - Useful in microservices or cloud-based applications for resilience.

3. **CQRS (Command Query Responsibility Segregation)**:

   - Separates read (query) and write (command) operations for independent scaling and optimization.
   - Example: E-commerce platforms with high read requests but fewer write operations.
   - Valuable in systems with different performance characteristics for read and write operations.

4. **Event Sourcing**:

   - Stores changes as a sequence of events, providing a complete history for auditing and debugging.
   - Example: Git version control system.
   - Enables features like time-travel debugging and event replay for analytics.

5. **Leader Election**:

   - Ensures only one node is responsible for a specific task or resource in a distributed system.
   - Example: ZooKeeper and etcd for managing distributed configurations.
   - Avoids conflicts and ensures consistent decision-making.

6. **PubSub (Publisher/Subscriber) Pattern**:

   - Publishers emit events without knowing subscribers, who listen for events they’re interested in.
   - Example: Google Cloud Pub/Sub for asynchronous messaging between services.
   - Ideal for updating multiple components or propagating changes.

7. **Sharding**:
   - Distributes data across multiple nodes to improve performance and scalability.
   - Example: MongoDB and Cassandra for handling large data volumes.
   - Enhances data locality and reduces network latency.

# How Discord Stores TRILLIONS of Messages

### Context and Challenge

- **Background**: Discord was using Cassandra for messaging but faced performance issues and maintenance challenges.
- **Task**: Migrate trillions of messages from Cassandra to ScyllaDB, a more efficient alternative.
- **Key Concerns**: Ensuring reliability and performance during and after migration.

### Strategy and Execution

1. **Preliminary Testing**:

   - Started with smaller databases to test and refine the migration process.
   - Approach: Move fast with reversible mistakes, but be cautious with significant changes.

2. **ScyllaDB Advantages**:

   - Written in C++, promising better performance and faster repairs.
   - Garbage collection-free, addressing a major pain point with Cassandra.

3. **Intermediate Data Services Layer**:

   - Written in Rust for safety and performance.
   - Implemented request coalescing to reduce database load and handle concurrent requests efficiently.

4. **Innovative 'Super-Disk' Solution**:

   - Created a custom disk solution combining Local SSDs (for low latency) and Persistent Disks (for durability) on Google Cloud.
   - Two-layered RAID setup: RAID0 for combining SSDs and RAID1 for mirroring with Persistent Disk.
   - Custom kernel configuration for optimized read and write operations.

5. **Migrating the 'Cassandra-Messages' Cluster**:
   - Used a custom-written data migrator in Rust.
   - Accomplished in nine days with no downtime.
   - Resulted in reduced node count and improved latencies.

### Outcomes and Benefits

- **Efficiency**: Reduced the number of database nodes significantly.
- **Performance**: Achieved better latencies and system reliability.
- **Operational Improvement**: Eased the load on the on-call team, improving overall quality of life.

### Lessons and Takeaways

- **Innovative Problem-Solving**: Discord's approach to redefining the problem and building a tailored solution (like the Super-Disk) is exemplary.
- **Risk Management**: Their phased and cautious approach to migration minimized potential risks.
- **Engineering Culture**: Reflects Discord's dynamic and innovative engineering ethos.

# Java vs Python vs C++

### C++: The Compiled Powerhouse

- **Compilation Process**: C++ code is compiled directly into machine code by a compiler.
- **Executable Files**: The output is a standalone executable file, ready to run on compatible systems.
- **Performance**: C++ is known for its high performance due to direct compilation to CPU instructions.
- **Use Cases**: Ideal for performance-sensitive applications like gaming, system-level programming, and applications where hardware-level manipulation is required.
- **Other Compiled Languages**: Go, Rust.

### Python: The Flexible Interpreter

- **Interpreted Nature**: Python code is executed on-the-fly by an interpreter.
- **Flexibility and User-Friendliness**: Offers ease of development and readability, making it a favorite for rapid prototyping and educational purposes.
- **Performance Trade-off**: Generally slower than compiled languages, as each line is interpreted at runtime.
- **Use Cases**: Widely used in web development, scripting, data analysis, and AI/ML applications.
- **Other Interpreted Languages**: JavaScript, Ruby, Perl.

### Java: The Hybrid Approach

- **Bytecode Compilation**: Java code is compiled into bytecode, which is then executed by the Java Virtual Machine (JVM).
- **JVM and JIT Compiler**: JVM's Just-In-Time compiler optimizes performance by converting critical bytecode into native machine code at runtime.
- **Portability**: Java code can run on any device with a JVM, making it highly portable.
- **Memory Safety and Security**: Automatic memory management and built-in security features make it suitable for large-scale, complex enterprise applications.
- **Use Cases**: Extensively used in Android app development, enterprise back-end systems, and large-scale web applications.
- **Other Bytecode Languages**: C#, Kotlin.

### Modern Trends and Blurring Lines

- **Advances in JIT**: Modern JavaScript engines use JIT compilation, blurring the lines between interpreted and bytecode languages.
- **Overall Classification**: JavaScript is still considered an interpreted language, but with performance optimizations.
