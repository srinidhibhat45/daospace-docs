+++
chapter = true
pre = "<b>2. </b>"
title = "Installation"
weight = 2
+++

### Installation


# Know how to install DaoSpace on your system
## Requirements
For development, you will need Node.js and a node global package, npm, installed in your environement.

### Node
- #### Node installation on Windows

  Just go on [official Node.js website](https://nodejs.org/) and download the installer.
Also, be sure to have `git` available in your PATH, `npm` might need it (You can find git [here](https://git-scm.com/)).

If the installation was successful, you should be able to run the following command.

    node --version
    v8.11.3

    npm --version
    6.1.0

If you need to update `npm`, you can make it using `npm`! Cool right? After running the following command, just open again the command line and be happy.

    npm install npm -g
    
## DB: MONGO ATLAS
    
   Atlas allows online access to the MongoDB via your IP access. Log in to your atlas before you run your project

## Stream Chat

  Installation:
### With npm
npm install stream-chat

### With Yarn
```yarn add stream-chat```

After installing the package, import the StreamChat module into your project and you're ready to go:

```
import { StreamChat } from 'stream-chat'

// or

const StreamChat = require('stream-chat').StreamChat
```
    
## Running the application

    git clone git@github.com:World-Konkani-Centre/SCL-2022-SHRESHTHA.git
    cd SCL-2022-SHRESHTHA
    
  Now, you need to install the packages both in client and server directory. 
  
    cd server
    npm i && start
    
    cd ..
   
    cd client
    npm i && start



### Team Shreshtha

 ##### Members:


###### Anirudha Kamath
###### K Avinash Nayak
###### Bhagavi Nayak
###### Karthik Mahale
###### Srinidhi Bhat (Team Lead)
###### Sushma
###### V Sahana Kamath