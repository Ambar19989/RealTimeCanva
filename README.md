# Collaborative Canvas (Real-Time)

Real-time collaborative drawing application built with HTML5 Canvas, Socket.IO (WebSocket), and Node.js.

## Features

- **Drawing Tools**: Brush and eraser with adjustable sizes (1–80px) and a color picker
- **Canvas Controls**: Undo/Redo (50 steps), clear canvas, download PNG
- **Real-Time Collaboration**: Multiple users can draw simultaneously in separate rooms
- **Synchronization**: Canvas state synchronizes across connected clients
- **User Awareness**: Join/leave notifications and cursor positions
- **Keyboard Shortcuts**: Ctrl+Z (Undo), Ctrl+Y (Redo), B (Brush), E (Eraser)
- **Cross-Device**: Works on desktop, tablets, and phones

## Setup Instructions

### Prerequisites

- Node.js v14+ and npm v6+

### Quick Start

```bash
npm install && npm start
```

This installs dependencies and starts the server (default: port 3000).

### Detailed Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/Ambar19989/RealTimeCanva.git
   cd collaborative-canvas
   ```

2. Install dependencies:

   ```bash
   cd Server
   npm install
   ```

3. Start the server:
   ```bash
   npm start
   ```

4. Open browser: `http://localhost:3000`

## Testing with Multiple Users

### Local Testing (Same Computer)

1. Start the server: `npm start`
2. Open multiple browser tabs and connect to the same room, e.g.:
   - `http://localhost:3000?room=test`
3. Draw in one tab and observe strokes appearing in the others.
4. Try different room names to isolate sessions.

### Network Testing (Multiple Devices)

1. Find your machine's local IP (e.g., `ipconfig` on Windows).
2. Start the server on that machine.
3. From other devices on the same network, open:
   - `http://<your-local-ip>:3000?room=test`
4. Draw on one device and confirm synchronization across devices.

## Limitations & Known Issues

### Limitations

1. **No persistent storage** — canvas state is in memory; drawings are lost on server restart.
2. **No authentication** — users are anonymous (User1, User2, etc.); no access control.
3. **Single-server** — not designed for horizontal scaling in the current setup.
4. **Eraser not synchronized** — eraser works locally to avoid conflicts.
5. **No rate limiting** — drawing event spam is not mitigated.
6. **No input validation** — drawing data is not validated on the server.
7. **Canvas size limits** — very large canvases can impact performance.

### Known issues

1. **Race condition on join** — a new user might miss the first strokes if joining during active drawing.
2. **Cursor delay** — cursor sync can lag on slow networks.
3. **Memory accumulation** — very long sessions may require server restart (auto-cleanup runs periodically).
4. **Mobile touch** — on some browsers touch drawing may cause page scrolling.

## Time Spent on Project

| Phase | Time | Tasks |
|-------|------|-------|
| Initial Setup & Research | 3h | Project structure, technology selection, WebSocket research |
| Core Drawing Logic | 4h | Canvas API, drawing tools, pointer events, undo/redo |
| WebSocket Integration | 3h | Socket.IO setup, event handling, client-server communication |
| Room System | 2h | Room manager, state persistence, multi-room support |
| Real-Time Sync | 4h | Drawing synchronization, state management, conflict handling |
| UI/UX Design | 3h | Responsive layout, toolbar, color picker, user feedback |
| Testing & Debugging | 4h | Multi-user testing, bug fixes, edge cases |
| Code Refactoring | 2h | Modular architecture, ES6 modules, clean code |
| Documentation | 2h | README, ARCHITECTURE |
| Polish & Features | 3h | Keyboard shortcuts, notifications, cursor sync |

### Total Time Spent

~30 hours

## Project Structure

```text
collaborative-canvas/
├── Client/
│   ├── index.html         # Main HTML
│   ├── style.css         # Styles
│   ├── canvas.js          # Drawing logic
│   ├── websocket.js       # WebSocket client
│   └── main.js           # App initialization
├── Server/
│   ├── Server.js          # Express + Socket.IO server
│   ├── rooms.js           # Room management
│   ├── drawing-state.js   # State persistence
│   └── package.json       # Dependencies
├── README.md
└── ARCHITECTURE.md
```

## Architecture

See [ARCHITECTURE.md](./ARCHITECTURE.md) for detailed system design.

**Technologies:**

- Frontend: HTML5 Canvas, ES6 Modules, Socket.IO Client
- Backend: Node.js, Express, Socket.IO
- Real-time: WebSocket (Socket.IO)
- State: In-memory

## License

ISC
