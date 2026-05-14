
# 🚦 Virtual Waiting Room (VWR) Control Center

A high-fidelity, real-time simulation of a **Gateway Traffic Controller** and **FIFO Queueing System**. This project demonstrates how to protect server infrastructure from traffic surges by implementing a virtual waiting room with strict concurrency constraints.

## 🚀 Project Overview
This application simulates a gateway script that monitors active user sessions. When the server reaches its `MAX_CAPACITY`, additional users are redirected to a synchronized queue and admitted one-by-one based on a defined `ADMIT_RATE`.

### Key Features
*   **Real-Time Dashboard:** Monitor active users, queue length, total served, and session timeouts.
*   **Automated Admission Logic:** A background "heartbeat" tick handles user promotion from queue to live site every 30 seconds.
*   **Session Management:** Automatic expiration of user sessions after 5 minutes to free up server slots.
*   **Traffic Simulation:** Built-in "Surge" tool to stress-test the queueing logic with rapid inbound requests.
*   **Visual Capacity Map:** A dynamic grid showing exactly which server slots are occupied and by whom.

## 🛠 Technical Constraints (Logic Rules)
The system is hard-coded to adhere to the following industrial-scale constraints:

| Parameter | Value | Description |
| :--- | :--- | :--- |
| **MAX_CAPACITY** | 10 | Max concurrent users allowed on site. |
| **ADMIT_RATE** | 2 / min | Users admitted from queue per 60 seconds (1 every 30s). |
| **SESSION_TIMEOUT** | 5 mins | Duration before a slot is forcefully vacated. |
| **QUEUE_TYPE** | FIFO | First-In, First-Out logic for fair access. |

## 💻 Tech Stack
*   **Frontend:** HTML5, CSS3 (Custom properties, Grid, Flexbox)
*   **Logic:** Vanilla JavaScript (ES6+)
*   **Typography:** Syne & JetBrains Mono for a "Command Center" aesthetic.

## 📖 How it Works
1.  **The Gateway:** When a user requests access, the system checks: `if (active_users < 10)`. 
2.  **The Redirect:** If the site is full, the user is pushed into the Queue.
3.  **The Wait:** The UI calculates an estimated wait time based on the user's position in line.
4.  **The Admission:** Every 30 seconds, the simulation "ticks," pulling the next available users from the queue into active slots.

## 🚦 Getting Started
1. Clone the repository.
2. Open `index.html` in any modern web browser.
3. Click **"Run Dataset A"** to watch the system handle a pre-defined surge of 25 users.
4. Adjust the **Speed Multiplier** (1x, 3x, 10x) to observe session timeouts and long-term queue behavior.

---
*Note: This project was developed as a technical demonstration of Rate Limiting and Queue Management logic.*
