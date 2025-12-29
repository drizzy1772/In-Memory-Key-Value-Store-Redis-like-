# In-Memory-Key-Value-Store-Redis-like-
TCP server built on gevent that implements key-value storage, similar to Redis. The server handles commands like GET, SET, etc. through a custom protocol. Data is stored in memory in ExpiringKeyValueStore, supports automatic deletion of expired keys. The client can connect to the server , fully separating the network layer from the storage logic.
