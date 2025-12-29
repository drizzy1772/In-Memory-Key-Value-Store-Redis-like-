🗄️ In-Memory Key-Value Store (Redis-like)

Lightweight in-memory key-value database with TTL support and a custom binary protocol.


✨ Features

💾 Key-value storage in memory
⏰ TTL support (SETEX) for auto-expiring keys
🔄 Batch operations (MGET, MSET)
📡 Custom Redis-like protocol
🌐 TCP client-server architecture
⚡ Concurrent connections with gevent
💿 Persistence with automatic snapshots
🔐 Atomic saves preventing data corruption

Architecture:

📨 ProtocolHandler — Parses and serializes protocol messages
💽 InMemoryKeyValueStore — Basic key-value storage
⏱️ ExpiringKeyValueStore — Storage with TTL support
🖥️ Server — Async TCP server handling commands
📱 Client — TCP client for interacting with the server


🚀 Tech Stack

🐍 Python 3
🌿 gevent (async networking)
🔌 TCP sockets
📦 Custom binary protocol
🧠 In-memory data structures
💾 Pickle persistence


📦 Installation
bashpip install gevent

▶️ Run Server
bashpython kvstore.py
```

Server starts on:
```
🌐 127.0.0.1:31337

💻 How to Use (Client API)
🔗 Connect from Python
pythonfrom kvstore import Client

client = Client()

📚 Commands Usage
📝 SET
Store a key-value pair
pythonclient.set("name", "Alice")
# Returns: 1
🔍 GET
Retrieve a value by key
pythonclient.get("name")
# Returns: "Alice"
⏰ SETEX
Store a value with TTL (in seconds)
pythonclient.execute("SETEX", "temp", 5, "data")
# Key expires after 5 seconds
🗑️ DELETE
Remove a key
pythonclient.delete("name")
# Returns: 1 (deleted) or 0 (not found)
📦 MSET
Set multiple key-value pairs
pythonclient.mset("a", "1", "b", "2", "c", "3")
# Returns: 3 (number of pairs set)
🔎 MGET
Get multiple values
pythonclient.mget("a", "b", "c")
# Returns: ["1", "2", "3"]
💥 FLUSH
Remove all keys
pythonclient.flush()
# Returns: number of keys deleted
💾 SAVE
Force immediate save to disk
pythonclient.save()
# Returns: "OK"
🌙 BGSAVE
Background save (non-blocking)
pythonclient.bgsave()
# Returns: "Background save started"
📊 DBSIZE
Get total number of keys
pythonclient.dbsize()
# Returns: 42
🕐 LASTSAVE
Get timestamp of last save
pythonclient.lastsave()
# Returns: 1735488000

🎯 Example Usage
pythonfrom kvstore import Client

# Connect to server
client = Client()

# Store data
client.set("user:1", "John")
client.set("user:2", "Jane")

# Batch operations
client.mset("x", "10", "y", "20", "z", "30")
values = client.mget("x", "y", "z")
print(values)  # ['10', '20', '30']


client.execute("SETEX", "session:abc", 3600, "token123")

# Check database size
print(f"Total keys: {client.dbsize()}")

# Save to disk
client.save()

REVIEW
# Temporary data with TTL<img width="813" height="484" alt="9999" src="https://github.com/user-attachments/assets/302f218e-9fc0-48f4-8d2f-7ea2b6b8ac9d" />






