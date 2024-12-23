# Basic Chat Application

This is a simple chat-based application built in **Node.js** using **Socket.IO**. The primary goal of this project was to understand the fundamentals of web sockets and real-time communication.

## Features
- Real-time messaging using web sockets.
- No UI (command-line or basic client-side testing through tools like Postman or browser console).
- Lightweight and minimal implementation focused on learning purposes.

## Tech Stack
- **Node.js**: Backend runtime environment.
- **Socket.IO**: Library for real-time, bidirectional communication between web clients and servers.

## Setup and Usage

### Prerequisites
- Node.js installed on your system.

### Installation
1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```
2. Install dependencies:
   ```bash
   npm install
   ```

### Running the Application
1. Start the server:
   ```bash
   node server.js
   ```
2. Open a browser or a WebSocket testing tool (e.g., Postman, browser console) and connect to the WebSocket server.

### How to Test
- Connect multiple clients to the server using WebSocket connections.
- Send messages from one client and observe real-time delivery to other connected clients.

## Example Code Snippets

### Server (Node.js):
```javascript
const http = require("http");
const express = require("express");
const path = require("path");
const { Server } = require("socket.io");

const app = express();
const server = http.createServer(app);
const io = new Server(server);

// Socket.io
io.on("connection", (socket) => {
  socket.on("user-message", (message) => {
    io.emit("message", message);
  });
});

app.use(express.static(path.resolve("./public")));

app.get("/", (req, res) => {
  return res.sendFile("/public/index.html");
});

server.listen(9000, () => console.log(`Server Started at PORT:9000`));
```

## Learning Outcomes
- Gained hands-on experience with WebSocket communication.
- Understood the basics of event-driven programming with Socket.IO.

## Future Improvements
- Add a simple UI to visualize chat messages.
- Implement user authentication and unique usernames.
- Enhance the message format with timestamps and user identifiers.

## License
This project is for learning purposes and does not include a formal license.

