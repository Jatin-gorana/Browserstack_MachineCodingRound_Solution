
# Tail-F Log Streaming using WebSockets

A simple implementation of the Linux `tail -f` command using **Python + WebSockets**.
This project streams log file updates to a browser in real-time.

---

##  Features

* Read last **N lines** of a file
* Real-time log streaming (`-f` option)
* WebSocket-based communication
* Simple frontend to display logs
* Adjustable polling interval
* Customizable port

---

##  Tech Stack

* Python 3
* asyncio
* websockets
* HTML + JavaScript

---

##  Project Structure

```
.
├── tailf.py        # Backend WebSocket server
├── logs.html       # Frontend log viewer
├── sample.log      # Sample log file
├── myscript.sh     # Optional script to run server
```

---

## ⚙️ Installation

###  Install dependencies

```bash
pip install websockets
```

---

## How to Run

### Step 1: Start the Python Server

```bash
python tailf.py sample.log
```

### With options:

```bash
python tailf.py sample.log -n 20 -f -p 8100 -s 1
```

### Arguments

| Argument | Description                        |
| -------- | ---------------------------------- |
| filename | Log file to stream                 |
| -n       | Number of last lines (default: 10) |
| -f       | Follow file in real-time           |
| -s       | Polling interval in seconds        |
| -p       | Port number (default: 8100)        |

---

### Step 2: Open Frontend

Open `logs.html` in your browser.

It connects to:

```
ws://localhost:8100
```

---

##  Example

Run:

```bash
python tailf.py sample.log -f
```

Now append something to `sample.log` and see it update live in the browser.

---

##  How It Works

1. Backend reads last N lines from file.
2. WebSocket server sends data to connected clients.
3. If `-f` is enabled, it continuously checks for new content.
4. Frontend listens to WebSocket messages and displays logs instantly.

---

##  Use Cases

* Monitoring application logs
* Debugging servers locally
* Learning WebSockets with Python
* Understanding file streaming logic

---

##  Notes

* Make sure the log file exists before running.
* If port 8100 is busy, use `-p` to change it.
* Works best on Python 3.8+

---
