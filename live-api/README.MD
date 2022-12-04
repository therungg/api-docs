# Live API

The Live API can be found at `https://therun.gg/api/live`. It returns a list of in-progress runs. 
It should be used in conjunction with the WebSocket API at `wss://fh76djw1t9.execute-api.eu-west-1.amazonaws.com/prod`.
The WebSocket API can be used to receive messages when a run changes. This prevents you from having to poll the HTTP API every x seconds.

If you only want to track the in-progress run for a specific runner, you can use `https://therun.gg/api/live/<username>` and `wss://fh76djw1t9.execute-api.eu-west-1.amazonaws.com/prod?username=<username>`

## Response format

I will document the response format later.
