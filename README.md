# rainbow
> (Idea stage) Modern, fast, stable, versatile, cross-platform torrent system based on rust, HTML5, javascript

## What is it?
Rainbow is meant to be a modern, fast, stable, versatile, and cross-platform torrent system.

## License
It will be based either on GPL3, or GPL2+ since this is not a small library.

## Technical
It will be based on rust, HTML5, javascript.

### Server
The rust part is the server daemon which handles everything via a JSON API.

#### Quality & Features:
It should at least support everything that uTorrent Pro supports.
It should have speed on par with rtorrent and be usable for seedboxes.

#### Server/Client separation:
The server should handle almost every operation in the system - everything that the GUI does
should be supported with high level operations if need be in the server.
For example, queueing and scheduling is in the servers domain and not the clients.

#### Rings, many servers, one interface:
There shouldn't just be one server... I've found myself having at least two torrent
servers running on two different computers - but I'd like to handle them with one interface.

Thus a decentralized ring system of servers should be used so that there's no single point of failure and that, for security purposes, the developers have no way to possibly reach the servers.

In the ring system, each server can relay the information from other servers.
In order to become a member of a ring, the server A sends a request to join a ring of another server B. This request could be done via email or via something with oauth feeling to it.
When the request is received and accepted, the server B chooses what ring to add the server A to. Thus you can have multiple rings and share a limited set of servers with some and a bigger set with others. When the server B accepts the request of A, it can determine if A is in turn allowed to add servers to that ring or if it simply can use the ring.

Another mode of sharing is read-only mode where the server that was added with this mode can only view, but not change, add, delete anything.

The clients should be able to add a torrent to ALL servers as if it was adding it to one.

### Web client
The web client will be based on simple HTML5 + client side javascript.

### Native client
The native client should be based on the web client. It might however need to use electron shell and some nodejs to provide a truly native feeling even tho it is javascript & HTML5.
Examples where this might be needed is dealing with local filesystem and permissions where client side javascript is just not enough if you want to access OS stuff that the web browser might not give access to. This however remains to be seen. The first stop is the web client.

### Console client
The sytem will also come with a console client that talks to the servers and will be developed after the GUI is done. The console client should be cross platform if possible.
The *nix side will be based on ncurses.