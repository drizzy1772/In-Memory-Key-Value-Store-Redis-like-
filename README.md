In-Memory-Key-Value-Store (Redis-like)

Lightweight in-memory key-value database with TTL support and a custom binary protocol.

Features

Key-value storage in memory

TTL support (SETEX)

Multiple operations (MGET, MSET)

Custom Redis-like protocol

TCP client-server architecture

Concurrent connections

Supported Commands

GET key

SET key value

SETEX key ttl value

DELETE key

MGET key1 key2 ...

MSET key1 value1 key2 value2 ...

FLUSH

Architecture

ProtocolHandler — parses and serializes protocol messages

InMemoryKeyValueStore — basic key-value storage

ExpiringKeyValueStore — storage with TTL support

Server — async TCP server handling commands

Client — TCP client for interacting with the server

Tech Stack

Python 3

gevent (async networking)

TCP sockets

Custom binary protocol

In-memory data structures

Installation
pip install gevent

Run Server
python kvstore.py


Server starts on:

127.0.0.1:31337

How to Use (Client API)
Connect from Python
from kvstore import Client

client = Client()

Commands Usage
SET

Store a key-value pair

client.set("name", "Alice")

GET

Retrieve a value by key

client.get("name")

SETEX

Store a value with TTL (in seconds)

client.execute("SETEX", "temp", 5, "data")

DELETE

Remove a key

client.delete("name")

MSET

Set multiple key-value pairs

client.mset("a", "1", "b", "2")

MGET

Get multiple values

client.mget("a", "b")

FLUSH

Remove all keys

client.flush()
