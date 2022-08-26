+++
chapter = true
pre = "<b>5. </b>"
title = "Features"
weight = 5
+++

### Chapter 2

# Some Chapter title

### Clients and Users

The first step to using the chat client is initializing a client and setting the current user. This is assigned default to the account name if not explicitly added in our code. (We need to create an account with GetStream.io)

### Channels

A channel contains messages, a list of people that are watching the channel, and optionally a list of members (for private conversations).

### Messages

Texts that goes into these channels are created using the sendMessage(). When you send a message to a channel, Stream Chat automatically broadcasts to all the people that are watching this channel and updates in real-time. You can also add attachments to the message. 

```
const text = 'I’m excited for the SCL project EXPO!';
 
const response = await channel.sendMessage({
    text,
    customField: '123',
});

```

The above three are the important documents which we store and retrieve using the user unique id. 
