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