# msgpack-rpc-node
MessagePack RPC implementation for Node
This package is a temporary fork of [theJian's package](https://www.npmjs.com/package/msgpack-rpc-node)
which fixes decode() failures when a TCP msg is fragmented across multiple packets.
It also upgrades to the latest @msgpack/msgpack version (2.7.2) and typescript v4. 

## Installation
```
$ npm install msgpack-rpc-node
$ yarn add msgpack-rpc-node
```

## Overview
```JavaScript
import { Server, TcpServer, Client, TcpClient } from 'msgpack-rpc-node';

const PORT = 3000;

// Create a server
const server = new Server({
  add(a, b) {
    return a + b;
  }
});

// Listen on port 3000
server.listen(TcpServer, PORT);


// Create a client that connects to port 3000 on localhost
const client = new Client(TcpClient, PORT);
await client.connect();

// Calling function add and passing 3 and 5 as arguments
const result = await client.call('add', 3, 5);
```

## License
MIT@theJian
