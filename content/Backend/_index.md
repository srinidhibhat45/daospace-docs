+++
chapter = true
pre = "<b>4. </b>"
title = "Backend"
weight = 4
+++

### Backend

# About the backend for the project

# Backend

- [<ins>Generating user tokens</ins>](https://getstream.io/chat/docs/node/#generating-user-tokens)
    
- [<ins>Syncing users</ins>](https://getstream.io/chat/docs/node/#syncing-users)
    

The chat API has some features that client side code can manage in specific cases but usually shouldn't. While these features can be initiated with client side code.

- [<ins>Syncing channels</ins>](https://getstream.io/chat/docs/node/#syncing-channels)
    
- [<ins>Adding & Removing members & moderators</ins>](https://getstream.io/chat/docs/node/#adding-members-or-moderators)
    
- [<ins>Sending messages</ins>](https://getstream.io/chat/docs/node/#sending-messages)
    
- [<ins>Changing App Settings</ins>](https://getstream.io/chat/docs/node/app_setting_overview/)
    

The backend has full access to the chat API.


### Generating user tokens

The backend creates a token for a user. You hand that token to the client side during login or registration. This token allows the client side to connect to the chat API for that user. Stream's permission system does the heavy work of determining which actions are valid for the user, so the backend just needs enough logic to provide a token to give the client side access to a specific user.


The following code shows how to instantiate a client and create a token for a user on the server:

```
// yarn add stream-chat
import { StreamChat } from 'stream-chat';
// if you're using common js
const StreamChat = require('stream-chat').StreamChat;
 
// instantiate your stream client using the API key and secret
// the secret is only used server side and gives you full access to the API
const serverClient = StreamChat.getInstance('sndzmeq3bywm','mcz4ezqjq83xh5y9m35xggaj28svyczgrgx4r4ahz9aqjkajmk27s58fp4z7ufby');
// you can still use new StreamChat('api_key', 'api_secret');
 
// generate a token for the user with id 'john'
const token = serverClient.createToken('john');
// next, hand this token to the client in your in your login or registration response

```

### Syncing users
When a user starts a chat conversation with another user both users need to be present in Stream's user storage. So you'll want to make sure that users are synced in advance. The update users endpoint allows you to update 100 users at once, an example is shown below:

```
const response = await client.upsertUsers([{ 
    id: userID, 
    role: 'admin', 
    mycustomfield: '123'
 }]);
 ```

Note that user roles can only be changed server side. The role you assign to a user impacts their permissions and which actions they can take on a channel.
 
### Syncing Channels
You can create channels client side, but for many applications you'll want to restrict the creation of channels to the backend. Especially if a chat is related to a certain object in your database. One example is building a livestream chat like Twitch. You'll want to create a channel for each Stream and set the channel creator to the owner of the Stream. The example below shows how to create a channel and specify the moderators:

```
const channel = client.channel(type, id, {
    created_by_id: '4645' 
})
await channel.create();
// create the channel and set created_by to user id 4645
const update = await channel.update({
    name: 'myspecialchannel',
    image: 'imageurl',
    mycustomfield: '123'
});
 ```

### Adding Members or Moderators
The backend SDKs also make it easy to add or remove members from a channel. The example below shows how to add and remove members:

```
await channel.addMembers(['thierry', 'josh']);
await channel.removeMembers(['tommaso']);
 
await channel.addModerators(['thierry']);
await channel.demoteModerators(['thierry']);
 ```

### Sending Messages
It's quite common that certain actions in your application trigger a message to be sent. If a new user joins an app some chat apps will notify you that your contact joined the app. The example below shows how to send a message from the backend. It's the same syntax as you use client side, but specifying which user is sending the message is required:

```
const toBeSent = {
    text: '@Josh I told them I was pesca-pescatarian. Which is one who eats solely fish who eat other fish.',
    attachments: [
        {
            type: 'image',
            asset_url: 'https://bit.ly/2K74TaG',
            thumb_url: 'https://bit.ly/2Uumxti',
            myCustomField: 123
        }
    ],
    mentioned_users: [josh.id],
    anotherCustomField: 234
};
const message = await channel.sendMessage({ ...toBeSent, user_id: 'john' });
```