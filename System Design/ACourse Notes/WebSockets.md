#systemdesign #websocket
- We can only have around 6 concurrent connections on a client browser.
- Only use 1 Websocket connection to do multiple use cases.
- Do the bare-minimum with web-sockets (connect with queues to deligate any work, dont have other persistent connections like DB connection pooling).
- Have a separate edge-server/service for websockets.
- One edge server can generally hold 50k socket connections.