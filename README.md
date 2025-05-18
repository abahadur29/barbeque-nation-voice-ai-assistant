# barbeque-nation-voice-ai-assistant
# 🧠 Barbeque Nation Conversational AI Assistant

This is a smart voice-based restaurant booking and support system for **Barbeque Nation**, built using **Retell AI**, **Cal.com**, **Pabbly**, and **Make.com**. The system handles user intents like table reservations, cancellations, rescheduling, complaints, and FAQs using conversational and multi-agent AI flows.

---

## 📌 Overview

- **Conversational Agent** (Retell AI): Voice interface that interacts with users.
- **Multi-Agent Flow**: Modular handling of tasks like booking, rescheduling, complaints, etc.
- **Calendar Booking** (Cal.com): Availability check and reservation.
- **Form Automation** (Pabbly.com): Used for linking booking data.
- **Workflow Automation** (Make.com): Backend flows for calling APIs, handling sheets, error recovery.

---

## 📐 Architecture Diagram

<img width="719" alt="Conversational Flow " src="https://github.com/user-attachments/assets/67a4de8a-a16f-498f-b90d-1b0df84c57b0" />


---

## 🛠️ Components Description

| Component     | Tool Used   | Purpose                                         |
|---------------|-------------|-------------------------------------------------|
| Voice Input   | Retell AI   | Interact with customer using a conversational UI |

| Booking       | Cal.com     | Check availability & confirm bookings           |
| Data Capture  | Pabbly.com  | Form-based input integration for Cal.com        |
| Automation    | Make.com    | Handles API calls, triggers, and logic flows    |
| Data Store    | Google Sheet| Stores outlet info, feedback logs, etc.         |

---

## 🔌 API Documentation

### 1. `discover_location(city, location)`
**Purpose**: Validates if the requested outlet exists  
**Inputs**: `city`, `location`  
**Returns**: Boolean (availability)  
**Trigger**: Called after collecting user location

---

### 2. `check_availability(city, location, datetime)`
**Purpose**: Check availability at the requested outlet and time  
**Inputs**: `city`, `location`, `datetime (ISO 8601)`  
**Returns**: Available slots or confirmation  
**Trigger**: Before booking or rescheduling

---

### 3. `book_reservation(city, location, datetime, name, email, pax)`
**Purpose**: Books a new table reservation  
**Inputs**: `city`, `location`, `datetime`, `name`, `email`, `pax`  
**Returns**: Booking confirmation  
**Trigger**: User confirms reservation details

---

### 4. `cancel_reservation(city, location, name, datetime)`
**Purpose**: Cancels an existing reservation  
**Inputs**: `city`, `location`, `name`, `datetime`  
**Returns**: Cancellation confirmation  
**Trigger**: Upon user cancellation request

---

### 5. `reschedule_reservation(city, location, name, old_datetime, new_datetime, email)`
**Purpose**: Reschedules an existing reservation  
**Inputs**: `city`, `location`, `name`, `old_datetime`, `new_datetime`, `email`  
**Returns**: Updated reservation details  
**Trigger**: User wants to change reservation timing

---

### 6. `escalate_complaint(city, location, details, callback_datetime)`
**Purpose**: Escalates complaints to store managers  
**Inputs**: `city`, `location`, `details`, `callback_datetime`  
**Returns**: Confirmation of escalation  
**Trigger**: User submits complaint or bad experience

---

## 🧪 Sample Conversation Flow
<img width="719" alt="Conversational Flow " src="https://github.com/user-attachments/assets/20b6152e-11c7-44d8-82d1-bf91990be1d7" />



---

## 🔁 Sample Reschedule Flow

<img width="655" alt="Screenshot 2025-05-18 172952" src="https://github.com/user-attachments/assets/964b2d00-1e57-4cf5-91ac-60a81fc751e4" />


---
## 📚 Knowledge Base Management

The knowledge base used for the conversational AI was originally provided by the company as a PDF document. To make it easy to manage and update, I converted the PDF into a CSV file and then compiled it into a master Google Sheet.

This Google Sheet serves as the centralized knowledge base for the system, allowing easy access, editing, and sharing of FAQs, menu details, and other relevant information. The chatbot references this master sheet to provide accurate and up-to-date responses.

> (https://docs.google.com/spreadsheets/d/1m-mGiZ3d3Kg0k4vHct_tAHqQ3syZtv48Elhvqsx__Z4/edit?usp=sharing)

This approach ensures that the knowledge base remains scalable and can be updated without disrupting the chatbot’s core functionality.


## 🗂️ Screenshots

🗓️ Cal.com – Bookings View* 
- <img width="950" alt="Screenshot 2025-05-18 174312" src="https://github.com/user-attachments/assets/d2a2219d-799f-43bc-9473-f61bd2ac9fef" />
- 📋 Cal.com – Event Types Configuration
- <img width="956" alt="Screenshot 2025-05-18 174322" src="https://github.com/user-attachments/assets/c5293cc3-869c-4b21-b9a3-4ad4bd45ce90" />
- ✅ Booking Confirmation UI
- <img width="335" alt="image" src="https://github.com/user-attachments/assets/4cf9bf55-9dbe-404e-ace6-4ed299557aee" />

 🔄 Reschedule Workflow — Fully implemented using multi-agent conversational design to manage rescheduling requests efficiently
- <img width="655" alt="Screenshot 2025-05-18 172952" src="https://github.com/user-attachments/assets/19516998-8339-4fde-a8a4-8dfb51f2fd12" />
 
- 🗣️ Voice Chat Interaction
- - <img width="227" alt="Screenshot 2025-05-18 171533" src="https://github.com/user-attachments/assets/77466b56-3ffb-4581-93dd-cbb1ed25713d" />
- <img width="218" alt="Screenshot 2025-05-18 171545" src="https://github.com/user-attachments/assets/dc934423-1236-4836-aa14-27a7bbb58219" />
- <img width="221" alt="Screenshot 2025-05-18 171558" src="https://github.com/user-attachments/assets/9d4e32a6-70bc-4d4a-9196-0167a6b0c0d9" />
  
- 🔗 Pabbly Form to Cal.com
- <img width="953" alt="Screenshot 2025-05-18 170816" src="https://github.com/user-attachments/assets/79bcb830-c625-41ae-b3b7-3d2e337faaaf" />
- <img width="533" alt="Screenshot 2025-05-18 170905" src="https://github.com/user-attachments/assets/41dae272-1639-4c77-9cfa-9d7ef3d82c58" />
- <img width="617" alt="Screenshot 2025-05-18 170924" src="https://github.com/user-attachments/assets/65c6c54a-73d8-4307-a87f-7576c17c5715" />
- <img width="560" alt="Screenshot 2025-05-18 170938" src="https://github.com/user-attachments/assets/1344a9ce-dd98-417b-bfb4-d36e428caf82" />

Additional Workflow Screenshot  
- <img width="347" alt="image" src="https://github.com/user-attachments/assets/bb1f9046-3f53-43e5-a0ea-ec1d77212638" />

---

## 🧾 Status

| Feature                     | Status     |
|----------------------------|------------|
| Multi-Agent Flow           | ✅ Complete |
| Retell AI Conversation     | 🟡 Partial  |
| Cal.com Booking Linkage    | ✅ Complete |
| Rescheduling Automation    | ✅ Complete |
| Error Recovery & Logging   | 🔄 In Progress |

---
---

## 📬 Author

Aditya Bahadur – B.Tech, Computer Science and Engineering, KIIT University  
Connect with me on [LinkedIn](https://www.linkedin.com/in/aditya-bahadur-b3b709197)

