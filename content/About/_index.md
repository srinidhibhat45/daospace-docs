+++
chapter = true
pre = "<b>1. </b>"
title = "About"
weight = 1
+++

### Chapter 2

# About DaoSpace

DaoSpace as the name suggests is a space for DAOs* to communicate efficiently and fluently in a manner most suitable to the technological involvements indulged by them as an organization. Although we noticed upon our research that there are several communication platforms outside: Slack and Discord to name a few, we also caught on to the fact that there is no such platform that facilitates DAO-related usage of the communication platform, i.e. having all tools accessible on the go, reducing the dependency on third-party apps and bots for most used features and hence we decided to develop DaoSpace to solve that exact problem.






**DAO: Member-owned communities without centralized leadership which provide a safe way to collaborate with internet strangers are also a safe place to commit funds to a specific cause.*

#### Why do we need DAOs?
Starting an organization with someone that involves funding and money requires a lot of trust in the people you're working with. But it’s hard to trust someone you’ve only ever interacted with on the internet. With DAOs you don’t need to trust anyone else in the group, just the DAO’s code, which is 100% transparent and verifiable by anyone.
This opens up so many new opportunities for global collaboration and coordination.

## Technology Stack
The project implementation will be done using MERN (MongoDB Express React NodeJS) stack. 
#### Client side
  React - A JavaScript library for building user interfaces<br>
#### Server side
  Node.js - evented I/O for the backend<br>
  Express.js - Fast, unopinionated, minimalist web framework for Node.js<br>
  MongoDB - The application data platform for NoSQL databases<br>
  Mongoose - used to facilitate mongodb integration<br>

## File structure
#### `client` - Holds the client application
- #### `public` - This holds all of our static files
- #### `src`
    - #### `assets` - This folder holds assets such as images, docs, and fonts
    - #### `components` - This folder holds all of the different components that will make up our views
    - #### `views` - These represent a unique page on the website i.e. Home or About. These are still normal react components.
    - #### `App.js` - This is what renders all of our browser routes and different views
    - #### `index.js` - This is what renders the react app by rendering App.js, should not change
- #### `package.json` - Defines npm behaviors and packages for the client
#### `server` - Holds the server application
- #### `env` - This holds our configuration files, like mongoDB uri
- #### `controllers` - These hold all of the callback functions that each route will call
- #### `models` - This holds all of our data models
- #### `routes` - This holds all of our HTTP to URL path associations for each unique url
- #### `app.js` - Defines npm behaviors and packages for the client
#### `package.json` - Defines npm behaviors like the scripts defined in the next section of the README
#### `.gitignore` - Tells git which files to ignore
