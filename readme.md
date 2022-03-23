# wstunnel
## WsTunnelUdp is a fork of [mhzed/wstunnel](https://github.com/mhzed/wstunnel)

Establish a UDP socket tunnel over web socket connection, for circumventing strict firewalls.

## Installation

npm install https://github.com/illusionfield/wstunnel.git

## Usage

Run the websocket tunnel server at port 8080 on all interfaces:

    wstunnel -s 0.0.0.0:8080

Run the websocket tunnel client:

    wstunnel -t 33:2.2.2.2:33 ws://host:8080

In the above example, client picks the final tunnel destination, similar to ssh tunnel. Alternatively for security reason, you can lock tunnel destination on the server end, example:

    Server:
        wstunnel -s 0.0.0.0:8080 -t 2.2.2.2:33

    Client:
        wstunnel -t 33 ws://server:8080

In both examples, connection to localhost:33 on client will be tunneled to 2.2.2.2:33 on server via websocket connection in between.

To tell client to connect via http proxy, do:

    wstunnel -t 33:2.2.2.2:33 -p http://[user:pass@]proxyhost:proxyport wss://server:443

For dev/test purpose, client can set '-c' option to disable ssl certificate check.

This also makes you vulnerable to MITM attack, so use with caution.

To get help, just run

    wstunnel
