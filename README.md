# BookTic

A high-performance, robust, and concurrent backend API for a **Cinema Ticket Booking System** built entirely using Go (Golang). This project demonstrates modern backend engineering principles, showcasing clean code architecture, data consistency under heavy concurrency, and a relational transactional model for processing seating allocations.

---

## 🚀 Key Features

* **Movie & Show Scheduling:** Full CRUD workflows for configuring Movies, Theaters (Cinemas), individual Audiences/Halls, and multi-category timed Showtimes.
* **Concurrency & Double-Booking Protection:** Implementation of robust transaction boundaries (or distributed keys) to completely mitigate race conditions when multiple users attempt to claim identical seats simultaneously.
* **Seat Allocation Lifecycle:** Temporary seat locking mechanics (e.g., holding selected seats for a 5-10 minute buffer during checkout simulation) which auto-expire via transactional checks.
* **Granular RBAC:** Role-Based Access Control enforcing distinct privileges for standard application Customers (browsing, checking availability, making reservations) versus System Administrators (adding titles, managing inventory, editing structural theater maps).

---

## 🛠️ Tech Stack & Architecture

* **Language:** Go (Golang) — utilizing native concurrency primitives like `goroutines` and strict context management.
* **Architecture:** Clean Architecture / Hexagonal Design principles ensuring a core domain boundary isolated from infrastructure frameworks, transport layers, and databases.
* **HTTP Routing:** Built using lightweight, idiomatic routing via performance-driven frameworks (e.g., Gin-Gonic or Chi).
* **Persistence & Schema Management:** Relational layout mapped with a standard structure supporting entity references (`Theaters -> Screens -> Shows -> Seats`).

---

## 📊 Database Schema Layout

The relational domain logic manages state changes across these core relational entities:

* **User:** `ID`, `Name`, `Email`, `PasswordHash`, `Role` (Admin/Customer).
* **Movie:** `ID`, `Title`, `Genre`, `Duration`, `Language`, `ReleaseDate`.
* **Theater:** `ID`, `Name`, `Location`.
* **Screen / Hall:** `ID`, `TheaterID`, `Name`, `TotalSeats`.
* **Show:** `ID`, `MovieID`, `ScreenID`, `StartTime`, `EndTime`.
* **Seat:** `ID`, `ScreenID`, `Row`, `Number`, `Category` (VIP, Standard).
* **Booking:** `ID`, `UserID`, `ShowID`, `TotalPrice`, `Status` (Pending, Confirmed, Cancelled).
* **ShowSeat (State Tracking):** `ShowID`, `SeatID`, `BookingID`, `Status` (Available, Locked, Booked), `LockedUntil`.

---

## 🛠️ Local Installation & Setup

### Prerequisites

* **Go** (v1.25.3 or higher recommended)
* A terminal setup environment (supports local environments or Android-based Termux)

### 1. Clone the Repository

```bash
git clone https://github.com/Sohan899/BookTic.git
cd BookTic

```

### 2. Verify Dependencies

Sync your local module dependencies and tidy up structural Go maps:

```bash
go mod tidy
go mod verify

```

### 3. Run the Application

Start up the local runtime environment to spin up the API web server:

```bash
go run cmd/main.go

```

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

### How to add this to your project:

1. Create a file named `README.md` inside your `cinema-ticket-booking` folder on your phone.
2. Paste this text inside it.
3. Save it, then push it to your repository using:
```bash

```



git add README.md
git commit -m "docs: add comprehensive system README"
git push origin main

```

```
