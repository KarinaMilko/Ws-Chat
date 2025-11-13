## 💬 ws-chat-realtime-messenger

This is a **full-featured messenger application** utilizing **Express.js** and **Socket.IO** to implement **real-time, bidirectional communication**. The project demonstrates the combination of a traditional REST API (for message history) with WebSockets (for instant CRUD operations).

---

### ⚙️ Technology Stack

| Component | Technologies | Purpose |
| :--- | :--- | :--- |
| **Backend (Server)** | Node.js, Express.js, MongoDB, Mongoose | Handles REST API and database logic. |
| **Real-Time** | Socket.IO | Manages bidirectional communication (WebSockets). |
| **Frontend (Client)** | React.js, Redux Toolkit, Formik | Client interface and global state management. |

---

### 1. 🚀 Real-Time Functionality (Socket.IO)

The `server/socket.js` file handles incoming client events, interacts with MongoDB, and broadcasts updates to all connected users.

| Event (Client → Server) | Server Action | Event (Server → All Clients) |
| :--- | :--- | :--- |
| `NEW_MESSAGE` | `Message.create(payload)` | `NEW_MESSAGE_SUCCESS` |
| `DELETE_MESSAGE` | `Message.findByIdAndDelete(id)` | `DELETE_MESSAGE_SUCCESS` |

---

### 2. ✅ Completed Tasks (Classwork & Homework)

| Category | Task | Description |
| :--- | :--- | :--- |
| **Creation** | Message Creation (`NEW_MESSAGE`) | Implemented via the Formik form in `App.jsx` and `ws.createMessage`. |
| **Deletion** | Message Deletion (`DELETE_MESSAGE`) | **(HOMEWORK)** Implemented real-time deletion on the server and instant Redux state update on all clients. |
| **Reading** | Message History | Uses **REST API** (`GET /api/messages`) and a Redux Thunk (`getMessagesThunk`) to load initial history. |

---

### 3. 🖥️ Client Logic (React/Redux)

* **Synchronization**: All `*_SUCCESS` events from Socket.IO trigger corresponding Redux Reducers (`newMessageSuccess`, `deleteMessageSuccess`) for **immediate UI updates**.
* **UX**: Implemented auto-scrolling to the latest message and logic to limit the number of messages stored in the Redux state (`state.limit`).
