# Vehicle Parking Management System

A Spring Boot-based web application designed to handle vehicle parking slot management, booking operations, payment processing, and reporting.

---

## Project Overview

This system allows users to:
- Register themselves and their vehicles.
- Book parking slots efficiently.
- Prevent double bookings and overlapping slots.
- Process and track payments.
- Generate usage and activity reports.

---

## Key Modules

- **entity/** : JPA Entity classes (`User`, `Vehicle`, `Booking`, `ParkingSlot`, `Payment`, `Report`).
- **repository/** : Spring Data JPA Repositories to interact with Apache Derby database.
- **controller/** : REST Controllers to expose application APIs.
- **dto/** : Data Transfer Objects to manage incoming and outgoing data.
- **service/** : Business logic implementation.
- **exception/** : Custom exception handling for clear error reporting.

---

## Technologies Used

- Java 17+
- Spring Boot
- Spring Data JPA (Hibernate)
- Apache Derby (Database)
- Lombok (for reducing boilerplate)
- Maven (build tool)

---

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/TejaswiniDama22/vehicle-parking-management.git
