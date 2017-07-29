# Sync a youtube player with chat messages

### Difficulty

Senior level JS engineer

### API

For this question, you have a given API which you need to mock completely, create fake data and make sure you test thoroughly.

#### Player

Instanciate a new player

`player = new Player()`

Get current time of video playing

`player.getCurrentTime()` Output should be an integer of seconds passed from video start time.

You will need to fake time passing so every time you call this function it will tick one second.

```
setInterval(() => { 
    console.log(player.getCurrentTime());
}, 1000);
```

Will print out 

```
1
2
3
4
5
6
```

Create a button that will jump the time of the player by 10-20 seconds randomly.

Hitting the button will mimic skipping the video.

```
1
2
3
4
5
6
// BUTTON CLICKED
17
18
19
// BUTTON CLICKED
30
```

### Chat messges

You have an API that returns all chat messages happened during a session.

`TwitchApi.getMessaged()`

```
[
    {
        timestamp: 1,
        message: "Hello",
        username: "someone"
    }
]
```

Messages timestamp is in milliseconds from the start of the session.

For the purpose of this interview, assume the start of the video and the start of the messages are perfectly in sync.

### Your solution

* Sync messages with video runtime.
* Fake all data in a way that will allow you to test this. You don't have API credentials yet, everything should be faked.
* When video is skipped, you need to dump all the messages that happened during this time to the chat window.

### Bonus

Show the messages and the video in a UI that makes sense for this and update in real time.

Talk about state update in an application like this and what are your challenges in building this.

Before you start working, talk about the architecture and what are the benefits of the solution you are about to implement.
