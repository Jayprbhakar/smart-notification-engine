# Smart Notification Engine — Project Submission Document

## 🔗 Project Links

* **GitHub Repository:** `https://github.com/Jayprbhakar/smart-notification-engine`
* **Backend Docker Hub:** `https://hub.docker.com/r/jaysdevdev/smart-notify-backend`
* **Frontend Docker Hub:** `https://hub.docker.com/r/jaysdevdev/smart-notification-engine`

---

## 🛠️ Project Overview & Architecture

A full-stack notification engine built with FastAPI, React, PostgreSQL, and Redis that prioritizes alerts, handles quiet hours scheduling, aggregates notifications, and tracks engagement.

* **Frontend UI:** `http://127.0.0.1:5173`
* **Swagger API Docs:** `http://127.0.0.1:8000/docs`

---

## 📄 Product Requirements Document (PRD)

### 1. Problem Statement
Users face notification fatigue due to un-prioritized, high-frequency alerts. The Smart Notification Engine prioritizes alerts based on keyword urgency, groups related notifications, schedules non-urgent alerts outside quiet hours, and tracks engagement.

### 2. Functional Deliverables
- **Priority Classification:** Rules engine prioritizing HIGH, MEDIUM, and LOW alerts based on title keywords and category tags.
- **Notification Grouping:** Aggregate notifications by category and hourly window to reduce spam.
- **Optimal Timing Scheduler:** Delivery suppression during quiet hours (10 PM - 7 AM), bypassing quiet hours only for HIGH priority alerts.
- **Engagement Analytics:** Track user interactions (`OPENED`, `DISMISSED`) to optimize delivery.

### 3. API Specifications

#### Ingest Notification
- **Endpoint:** `POST /api/notifications/ingest`
- **Payload:**
  ```json
  {
  "user_id": 3,
  "grouped_notifications": {
    "social:2026-08-24-21": [
      {
        "id": 10,
        "user_id": 3,
        "title": "outdoor",
        "message": "let go for ride",
        "category": "social",
        "priority": "MEDIUM",
        "group_key": "social:2026-08-24-21",
        "status": "DELIVERED",
        "created_at": "2026-08-24T15:42:53.962897"
      }
    ]
  }
}