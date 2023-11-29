#### Envoy draining test with websockets

## Install websocketd
```brew install websocketd```

## Start up the websocket server
```./run.sh```

## Start up envoy in a new terminal
```envoy -c ./envoy.yaml```

## Open the browser 
```open ./browser.hml```

The count should be incrementing...

Now start draining, in another new terminal

```curl -X POST localhost:9901/drain_listeners```

More info: https://www.envoyproxy.io/docs/envoy/latest/operations/admin#operations-admin-interface-drain

The existing browser window should continue working,
if we refresh or try to open a new browser, there will be no response.