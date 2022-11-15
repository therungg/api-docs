# Marathon API

The Marathon API is a personalized WebSocket API that sends messages representing Stream Events to its listeners. 
Events are triggered when they get manually emitted from a custom-built Marathon Dashboard. 
The data on this dashboard is fed from the [LiveSplit Component](https://github.com/therungg/LiveSplit.TheRun).
The API can be listened to from a backend with the intent of initiating an action on the marathon's end: to show data on stream, to transmit data to the runner/commentators, or to inform production.

## Before we begin

The API feeds you data for a currently in-progress run, as tracked by the LiveSplit Component. 
This means that if you want to show live data about a certain runner, they must be using LiveSplit with the Component, or they will not show up on the Dashboard.

Also, the tool works best when the runner has at least a few finished runs in the category that's currently being played. More data -> more cool info to show.

## How to use

First, we're going to setup listening to the WebSocket API. Then, we'll learn how to send some events your way!

### Setting up the API

The API you connect to is personalized for your Twitch account. You can access it by making a websocket connection to:

`wss://fh76djw1t9.execute-api.eu-west-1.amazonaws.com/prod?username=marathon-< twitchUsername >`

where < twitchUsername > should be subsituted by the Twitch username you will login with (case sensitive!). I recommend using something like `wscat -c <url>` to test it out. 
Then, use your favorite WebSocket tool for your language of choice to listen to the API from your end. For example, 
I use [react-use-websocket](https://www.npmjs.com/package/react-use-websocket) for React, which is a handy little wrapper for the [JS WebSocket Object](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket).

When setup properly, you will receive messages everytime an event is triggered from the Dashboard. This can be done by streamers, production, anyone you want to allow control over the actions you defined.


### Sending events to your listener
Next, we will learn how to transmit events to the listener we just set up.

1. Login to [The Run](https://therun.gg) with Twitch.
2. Navigate to the Marathon Dashboard at https://therun.gg/marathon. Your personalized API will already be good to go.
3. Select the name of the runner you would like to trigger events for. You can also enter the name of the runner, in case they are not running yet. The page will update automatically once they do start running. Usually, the account you're looking for will be the account that's coupled to the Upload Key you entered into LiveSplit.
4. You're now all set to start sending events to your listener. Try out hitting one of the big green buttons to see if you receive any data :)


# Types of events

There's a bunch of events that you can transmit to your listener. 
For example, you can send a message when the runner you're tracking got a Gold Split, when they are ahead of their PB, when a RNG-heavy split is coming up, and much more.
Also, throughout the run, you can transmit events that just show some general data. You want to know how many times this runner has attempted and finished runs in this category? How long the last split takes them on average? There's events for this, and for much more.

Check the /events directory for TypeScript interfaces for each event (informative!) plus .json samples for every event.

## All events
Many more events will be added in the future. Contact me if you want some custom added. Also, if you need different/new data for any given event, also let me know.

- general_data_event
- live_data_event
- run_started_event
- gold_split_event
- best_run_ever_event
- top_10_single_segment_event
- top_10_total_segment_event
- worst_10_single_segment_event
- final_split_event
- run_ended_event