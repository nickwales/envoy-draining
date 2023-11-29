#### Envoy draining test with websockets

## Install websocketd and websocat
```
brew install websocketd
brew install websocat
```

## Start up the websocket server
```./run.sh```

## Start up envoy in a new terminal
`envoy -c ./envoy.yaml`

## Open the first client in a new terminal
`websocat ws://127.0.0.1:8443`

The count should be incrementing...

Now start draining, in another new terminal

`curl -X POST "localhost:9901/drain_listeners?graceful"`

In the same terminal attempt to start a second client
`websocat ws://127.0.0.1:8443`

which will fail with error:
```
websocat: WebSocketError: I/O failure
websocat: error running
```


More info: https://www.envoyproxy.io/docs/envoy/latest/operations/admin#operations-admin-interface-drain
