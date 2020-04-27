---
title: "React Express Socketio"
date: 2020-04-27T15:08:17+01:00
tags: [react, socket.io, nodejs, expressjs, websockets]
---

**Requirements**:

1. Create a React application and run it to get default page

2. Remove all extant files

3. Create a new `App.js` starter file

4. Add socket-io to `server.js`

5. Add socket-io-client to `App` component

6. Send 'Welcome!' message on client connect 

7. Render 'Welcome!' message from the server


**Tech**:

- nodejs
- npm
- npx
- react (create-react-app)
- socket.io (socker-io)
- socket.io-client (https://www.npmjs.com/package/socket.io-client)

**References**

- [socket-react](https://www.valentinog.com/blog/socket-react/)

**Hint 1**

Add to App.js:

```js
import React, { useState, useEffect } from "react"
import socketIOClient from "socket.io-client"
const ENDPOINT = "http://127.0.0.1:4001"

function App() {
  const [message, setMessage] = useState("")

  useEffect(() => {
    const socket = socketIOClient(ENDPOINT)
    socket.on("welcome-evt", data => {
      setMessage(data);
    })
  }, [])

  return (
    <p>
      {message}
    </p>
  );
}

export default App
```

**Hint 2**

Add to server.js:

```js
const express = require("express")
const http = require("http")
const socketIo = require("socket.io")
const port = process.env.PORT || 4001
const index = require("./routes/index")
const app = express()
app.use(index)

const server = http.createServer(app)
const io = socketIo(server)

io.on("connection", (socket) => {  
  socket.emit("welcome-evt", "Welcome!")
  socket.on("disconnect", () => {
    console.log("Client disconnected")    
  })
})
```