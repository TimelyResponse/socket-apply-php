## Installing

Preferred way to install is with [Composer](https://getcomposer.org/).
```
composer require textalk/websocket
```
## Client

The [client](docs/Client.md) can read and write on a WebSocket stream.
It internally supports Upgrade handshake and implicit close and ping/pong operations.

```php
$client = new WebSocket\Client("ws://echo.websocket.org/");
$client->text("Hello WebSocket.org!");
echo $client->receive();
$client->close();
```

## Server

The library contains a rudimentary single stream/single thread [server](docs/Server.md).
It internally supports Upgrade handshake and implicit close and ping/pong operations.

Note that it does **not** support threading or automatic association ot continuous client requests.
If you require this kind of server behavior, you need to build it on top of provided server implementation.

```php
$server = new WebSocket\Server();
$server->accept();
$message = $server->receive();
$server->text($message);
$server->close();
```
