<h1 align="center">⏰ Deadline Reminder App</h1>

<p align="center">
  <strong>An active, real-time desktop task management and alert system built with Python.</strong><br>
  Eliminate missed deadlines with dual-layered audio and mobile email notifications, interactive visual scheduling, and automated productivity tracking.
</p>

---

## 📖 Overview
The **Deadline Reminder App** is a lightweight, professional desktop application designed to solve the problem of passive to-do lists. Instead of waiting for users to manually check their schedules, this application runs a non-blocking background engine that continuously monitors system time. When a deadline hits, it triggers a fail-safe dual-alert system—a looping local audio alarm and an automated email dispatched directly to your mobile device. 

It features a modern GUI with interactive analog clocks, visual calendars, and dynamic analytical dashboards to track your punctuality (On-Time, Late, or Missed).



## ✨ Key Features
*   **Dual-Layered Alerts:** Guarantees you never miss a deadline. Uses `pygame` for a loud local audio alarm and `smtplib` to route automated email alerts containing task details to your phone.
*   **Live Analytical Dashboard:** Instantly tracks your workload, updating the total count of Active Deadlines, Completed Tasks, and Missed Deadlines in real-time.
*   **Error-Free Scheduling:** Replaces manual text entry with `tkcalendar` and `tktimepicker`. Set deadlines visually by clicking a calendar and dragging the hands of a digital analog clock.
*   **Visual Accountability & Tracking:** Permanently archives completed tasks using a lightweight `JSON` database. Automatically color-codes your history log to reflect your exact punctuality (🟢 On-Time, 🟠 Done Late, 🔴 Missed).
*   **Conflict-Free Identity Management:** Secures all task data using Python's `uuid` library. Every task is assigned a hidden 32-character ID, allowing you to create, edit, or delete identically named tasks without database conflicts.

## 💻 Technology Stack
*   **Backend Engine:** Python 3 (Real-time `.after()` loops, `datetime`, `uuid`)
*   **Frontend GUI:** Tkinter & CustomTkinter (`ttk` themes)
*   **Visual Widgets:** `tkcalendar`, `tktimepicker`
*   **Audio Processing:** `pygame.mixer` (Asynchronous cross-platform MP3 playback)
*   **Network / Alerts:** `smtplib`, `email.mime` (SMTP Google App Password Authentication)
*   **Database:** `json`, `os` (Offline, lightweight local persistence)

---

## 🚀 Installation & Setup

### Prerequisites
Make sure you have [Python 3.x](https://www.python.org/downloads/) installed on your system.

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/deadline-reminder-app.git
cd deadline-reminder-app
```

### 2. Install Required Libraries
Open your terminal or command prompt and install the necessary external Python libraries by running:
```bash
pip install tkcalendar pygame tktimepicker
```
*(Note: If `tktimepicker` fails to install on your system, the application is designed to safely fall back to standard spinboxes automatically).*

### 3. Configure Email Alerts (Optional but highly recommended)
To enable the application to send automated email alerts to your phone:
1. Open the main python file (e.g., `main.py`) in any text editor.
2. Locate the **Developer Configuration** section near the top of the file.
3. Replace `APP_SENDER_EMAIL` with your Gmail address.
4. Replace `APP_SENDER_PASSWORD` with a 16-character **Google App Password**. 
   * *Security Note: Do not use your standard email password. Generate a secure App Password via your Google Account -> Security -> 2-Step Verification -> App Passwords.*

### 4. Run the Application
Once the libraries are installed, you can start the application by running:
```bash
python main.py
```

---

## 🛠️ System Architecture
The application is built on a highly modular 3-tier architecture to prevent UI freezing during alert triggers:
1.  **Presentation Layer:** The Tkinter dashboard captures user inputs securely via visual widgets and instantly renders local `JSON` data onto Treeview tables.
2.  **Business Logic Engine:** A thread-safe `1000ms` background polling loop evaluates the live system clock against stored deadlines. 
3.  **Data & Output Layer:** Upon reaching a deadline, the engine asynchronously fires `pygame` and `smtplib` alerts while securely updating task status using UUID targeted JSON rewriting.

## 🔮 Future Scope
*   **Cloud Synchronization:** Transitioning to Firebase to sync active deadlines across multiple desktop workstations.
*   **External API Integration:** Bi-directional syncing with Google Calendar and Microsoft Outlook APIs.
*   **Advanced Analytics:** Auto-generating weekly productivity reports exported as PDF/Excel.

---
**Developed by:** Umang Kumar Singh
