---
title: Blockchain with NodeJS
date: 2019-05-01
publishdate: 2019-03-01
author: Pownthep Laokhunthot
description: This post will show you how to create REST API endpoints using the Express framework on Node JS, set up a Blockchain for development purposes using Multichain, and get started on journey develop decentralized application.
tags: 
    - javascript
    - node
    - multichain
---
# Blockchain with NodeJS
## Goals

1. Create REST API endpoints using the Express framework on Node JS
2. Set up a Blockchain for development purposes using Multichain
3. Get started on journey develop decentralized application

## Requirements
- A local computer

## Install Node JS
Download and install Node JS from their official website: https://nodejs.org/en/.

## Create an Express application
Express is a javascript backend framework for building REST API endpoints.

### Install Express
Open Terminal (macOS) or Command Prompt (Windows). <br>
```bash
cd Desktop
``` 
This command navigates you inside the Desktop folder.
```bash
mkdir express
```
This command creates a folder named "express".
```bash
cd express
```
This command navigates into the "express" folder.
```bash
npm init -y 
```
This command creates a `package.json` file which contains meta data about your project and what packages your project uses.
```bash
npm install express --save
```
This command tells NPM (Node Package Manager) to `install` Express and `--save` updates the `package.json` to include Express as a project dependency. 
```bash
touch index.js
```
This will create an `index.js` file.

### Create index.js file
Now open `index.js` in any code editor of your choice (VS Code).
Copy and paste the following code.
```javascript
const express = require('express')
// Import the express package so you can use it.

const app = express()
// Initialize app as an express app.

const port = 3000
// Set port number.

app.get('/', (req, res) => res.send('Hello World!'))
// Create a REST API endpoint for a GET request 
// that would return the string "Hello World!".

app.listen(port, () => 
    console.log(`Example app listening on port ${port}!`))
// Start listening for requests on port 3000.
```
On your Terminal or Command Prompt.
```bash
node index.js
```
Now open a browser and type in.
```
http://localhost:3000
```
You should see `Hello World!`

## Setup Blockchain with Multichain
Multichain is an open platform for building blockchain and from my experience it is by far the easiest to install and setup.
### Setup on Windows 10
#### Download Multichain
- https://www.multichain.com/download/multichain-windows-2.0.1.zip.

#### Install Multichain
- Extract the multichain-windows-2.0.1.zip.
- Open Command Prompt.

```bash
cd multichain-windows-2.0.1
```
Navigate into multichain folder.
```bash
multichain-util create chain1
```
This command create a Multichain configuration file that will be use when we start the Blockchain. **_'chain1'_** is the name of the Blockchain.
```bash
multichaind chain1 -daemon
```
This command starts the **_'chain1'_** Blockchain. It should show something like this. **_Note that the IP and port number be different for you._**
```plaintext
MultiChain 2.0.1 Daemon (Community Edition, latest protocol 20009)

Looking for genesis block...
Genesis block found

Other nodes can connect to this node using:
multichaind chain1@25.57.251.107:6737

This host has multiple IP addresses, so from some networks:
multichaind chain1@10.0.75.1:6737
multichaind chain1@192.168.56.1:6737
multichaind chain1@172.19.74.145:6737
multichaind chain1@192.168.1.3:6737

Listening for API requests on port 6736 (local only - see rpcallowip setting)

Node ready.
```
In order for us to connect to the Blockchain using the Express application, we are going need 3 things:


1. API requests port
2. Username
3. Password

#### API requests port
Remember the port number that the Blockchain will listen for API requests. In my case, the port is **_6736_**.

#### Username & Passwrod
The password is randomly generated when we run `multichaind chain1 -daemon`, so we need to look at the **_multichain.conf_** file.

You can find the file in **_"User/YOURUSERNAME/Roaming/Multichain/chain1/multichain.conf"_**. Replace _YOURUSERNAME_ with your own username.
```plaintext
rpcuser=multichainrpc
rpcpassword=2FEKaUyPSf5GAb8XEaiQgy7SY2ZEZQ4GVfTDtfRDqQYT
```
So in my case, the username is _"multichainrpc"_ and the password is _"2FEKaUyPSf5GAb8XEaiQgy7SY2ZEZQ4GVfTDtfRDqQYT"_

### Setup on macOS
_Coming soon_
## Create Multichain REST API endpoints
Now it's time to go back our Express application and implement some Multichain REST API endpoints.

### Install multichain-node
- Open Terminal or Command Prompt
- Navigate to the Express app folder
- Run `npm install multichain-node --save`
- Open _index.js_ and paste the following code

```javascript
let multichain = require("multichain-node")({
    port: 6736, // TODO: Replace with the port you got from the last step
    host: '127.0.0.1',
    user: "multichainrpc", // TODO: Replace with the username you got from the last step
    pass: "2FEKaUyPSf5GAb8XEaiQgy7SY2ZEZQ4GVfTDtfRDqQYT" // TODO: Replace with the password you got from the last step
});
// Import and initialize Multichain.

const express = require('express')
// Import the express package so you can use it.

const app = express()
// Initialize app as an express app.

const port = 3000
// Set port number.

app.get('/', (req, res) => res.send('Hello World!'))
// Create a REST API endpoint for a GET request 
// that would return the string "Hello World!".

app.get('/multichain', (req, res) => {
    multichain.getInfo((err, info) => {
        if(err){
            throw err;
        }
        res.json(info);
    })
})
// Create a REST API endpoint for a GET request 
// that would return the information about the blockchain.

app.listen(port, () => 
    console.log(`Example app listening on port ${port}!`))
// Start listening for requests on port 3000.
```
Now if open your browser and navigate to _http://localhost:3000/multichain_

Voila!!! you are done.