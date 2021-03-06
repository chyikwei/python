## Contact support@pubnub.com for all questions

#### [PubNub](http://www.pubnub.com) Real-time Data Network
##### Tornado Migration

#### Import

```
# Pre 3.5:
from pubnub import Pubnub

# New in 3.5+
from pubnub import PubnubTornado as Pubnub

```


#### Init

```

# Pre 3.5:
pubnub = Pubnub(
    "demo",  ## PUBLISH_KEY
    "demo",  ## SUBSCRIBE_KEY
     False   ## SSL_ON?
)

# New in 3.5+
pubnub = Pubnub(publish_key="demo", subscribe_key="demo", ssl_on=False)

```

#### PUBLISH

```
channel = 'hello_world'
message = 'Hello World !!!'

# Pre 3.5:
def callback(messages):
    print(messages)

pubnub.publish( {
    'channel'  : channel,
    'message'    : message,
    'callback' : callback
})

# New in 3.5+

def callback(message):
    print(message)

pubnub.publish(channel, message, callback=callback, error=callback)

```


#### SUBSCRIBE

```

# Listen for Messages

channel = 'hello_world'

# Pre 3.5:
def connected() :
    print('CONNECTED')

def message_received(message):
    print(message)

pubnub.subscribe({
    'channel'  : channel,
    'connect'  : connected,
    'callback' : message_received
})

# New in 3.5+

def callback(message, channel):
    print(message)


def error(message):
    print("ERROR : " + str(message))


def connect(message):
    print("CONNECTED")


def reconnect(message):
    print("RECONNECTED")


def disconnect(message):
    print("DISCONNECTED")


pubnub.subscribe(channel, callback=callback, error=callback,
                 connect=connect, reconnect=reconnect, disconnect=disconnect)
```

#### Unsubscribe
Once subscribed, you can easily, gracefully, unsubscribe:

```
# Pre 3.5:
pubnub.unsubscribe({
    'channel' : 'hello_world'
})

# New in 3.5+

pubnub.unsubscribe(channel='hello_world')
```

#### PRESENCE

```

# Pre 3.5:
#

# New in 3.5+

# Listen for Presence Event Messages

channel = 'hello_world'

def callback(message, channel):
    print(message)


def error(message):
    print("ERROR : " + str(message))

pubnub.presence(channel, callback=callback, error=callback)
```

#### HERE_NOW

```

channel = 'hello_world'

# Pre 3.5:
def callback(messages):
    print(messages)

pubnub.here_now( {
    'channel'  : channel,
    'callback' : callback
})


# New in 3.5+

# Get info on who is here right now!


def callback(message):
    print(message)

pubnub.here_now(channel, callback=callback, error=callback)
```

#### HISTORY

```
channel = 'hello_world'

# Pre 3.5:
def history_complete(messages):
    print(messages)

pubnub.history( {
    'channel'  : channel,
    'limit'    : 2,
    'callback' : history_complete
})


# New in 3.5+

def callback(message):
    print(message)

pubnub.history(channel, count=2, callback=callback, error=callback)
```

#### IO Event Loop

```

# Pre 3.5:
tornado.ioloop.IOLoop.instance().start()

# New in 3.5+
pubnub.start()
```
## Contact support@pubnub.com for all questions
