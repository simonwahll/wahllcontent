---
title: "Socket Server"
description: "Socket Server"
lead: ""
date: 2021-05-01T13:10:28+02:00
lastmod: 2021-05-01T13:10:28+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Server"
weight: 200
toc: true
---

It is really easy to create a socket server in Dart. But what is a socket? A socket is like a pipe between two computers over the network. Data can be sent in both directions without having the client make a request for data, like with HTTP. This allows us to build software where data is updated quite randomly and when data needs to be sent to the client as fast as possible, like a chat application.

Dart can be used to build both the server and the client when using sockets. Since Dart is a high-level language there are lots of abstraction layers on top of the socket logic that makes it a lot easier to use, at the cost of control. If you have some use case where you need more control over the socket you can still use Dart without these abstraction layers but this will not be covered in this tutorial.

## Socket Server

To create a socket server you need to follow these steps:

1. Create a `ServerSocket` object and bind an IP address and a port to this object. The `ServerSocket.bind()` method creates this object and binds the IP address and the port to it at the same time.

2. Call the `listen()` method on the `ServerSocket` object with a function as a parameter. This function receives a `Socket` object as an argument. This is the object that can be used to communicate with the client.

3. Connect three functions to the `listen()` method on the `Socket`. These are `onData`, `onError` and `onDone`.

4. The `onData` function receives a `Uint8List` with the data received from the client. This [list]({{< ref "/dart/dart/lists" >}} "Dart Lists") can be converted into a [String]({{< ref "/dart/dart/data_types#string" >}} "Dart Strings") with the `String.fromCharCodes()` method.

5. The `onError` function receives an error object with the error information. The error can be handled here or alternatively, the socket can be closed with the `close()` method.

6. The `onDone` function is called when the connection has been closed.

7. Data can be sent to the client with the `write()` method on the `Socket` object.

Let's put this together into a `Server` class.

```dart
import 'dart:io';
import 'dart:typed_data';

class Server {
  ServerSocket _server;
  final List<Socket> _clients = [];
  final _ipAddress = InternetAddress.anyIPv4;
  final _port = 1234;

  Server() {
    _startServer();
  }

  void sendData(Object data) {
    // The write() method will call the toString()
    // method on the data object. It will then send
    // the data over the socket to the client.
    _clients.forEach((client) => client.write(data));
  }

  void _startServer() async {
    // ServerSocket.bind() returns a Future. Await the 
    // result of this Future.
    _server = await ServerSocket.bind(_ipAddress, _port);

    print('Server started on ${_ipAddress.address}:$port');

    // Start listening to incoming connections to
    // clients. Add new clients to the _clients list
    // and call the _handleNewClient method with the
    // new client.
    _server.listen((Socket client) {
      _clients.add(client);
      _handleNewClient(client);
    });
  }

  void _handleNewClient(Socket client) {
    // Assigns a lambda (Function) to a variable.
    // This lambda can be async so it does not block
    // when running. It will handle incoming data
    // from the client. When receiving a message
    // from the client it will also send a message
    // back.
    var onData = (Uint8List data) async {
      var decodedData = String.fromCharCodes(data);
      print('Received: $decodedData');
      sendData("Hello from the server");
    };

    // This lambda will run when an error has occured.
    var onError = (error) {
      print(error.toString());
      client.close();
    };

    // This lambda will run when the connection to
    // the client has been closed.
    var onDone = () {
      print('Connection closed');
      client.close();
    };

    // Connect these lambdas to the listen() method on 
    // the client.
    client.listen(onData, onError: onError, onDone: onDone);
  }
}
```

You can read about lambdas [here]({{< ref "/dart/dart/lambda" >}} "Dart Lambdas").

This class can be started with this `main()` function:

```dart
import 'server.dart';

void main() {
  var server = Server();
}
```

## Socket Client

Connecting a client to a server is similar to the server. These are the steps:

1. Create a `Socket` object and call the `connect()` method on it with an IP address and a port to connect to as two parameters. The `connect()` method creates this object and connects it to the server at the same time.

2. Connect three functions to the `listen()` method on the `Socket`. These are `onData`, `onError` and `onDone`.

3. The `onData` function receives a `Uint8List` with the data received from the server. This [list]({{< ref "/dart/dart/lists" >}} "Dart Lists") can be converted into a [String]({{< ref "/dart/dart/data_types#string" >}} "Dart Strings") with the `String.fromCharCodes()` method.

4. The `onError` function receives an error object with the error information. The error can be handled here or alternatively, the socket can be destroyed with the `destroy()` method.

5. The `onDone` function is called when the connection has been closed.

6. Data can be sent to the server with the `write()` method on the `Socket` object.

Let's put this together into a simple program.

```dart
import 'dart:io';
import 'dart:typed_data';

void main() async {
  var ipAddress = 'localhost';
  var port = 1234;
  var socket = await Socket.connect(ipAddress, port);

  print('Connected to $ipAddress:$port');

  var onData = (Uint8List data) {
    var decodedData = String.fromCharCodes(data);
    print('Received: $decodedData');
  };

  var onError = (error) {
    print(error.toString());
    socket.destroy();
  };

  var onDone = () {
    print('Connection closed');
    socket.destroy();
  };

  socket.listen(onData, onError: onError, onDone: onDone);

  socket.write('Hello from the client');
}
```

The `onData`, `onError`, and `onDone` lambdas are connected to the `Socket` object with the `listen()` method, exactly the same as on the server. Sending data to the server is also done in the same way as sending data from the server to the client, with the `write()` method on the `Socket` object.

## Testing Our Sockets

Start by running the server code and then start the client code.

Server output:

```
$ dart run server.dart
> Server started on 0.0.0.0:1234
> Received: Hello from the client
```

Client output:

```
$ dart run client.dart
> Connected to localhost:1234
> Received: Hello from the server
```

You can close these programs with `Control+C`.