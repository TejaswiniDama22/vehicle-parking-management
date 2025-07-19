# Vehicle Parking Management System

A Spring Boot project for managing vehicle parking, booking slots, handling payments, and generating reports. This project uses Hibernate/JPA for ORM and follows a modular entity structure.

##  Project Structure

- **entity/**
  - `Booking.java` – Manages slot bookings.
  - `ParkingSlot.java` – Tracks slot availability and type.
  - `Payment.java` – Handles payment details.
  - `Report.java` – Generates user-related reports.
  - `User.java` – Stores user registration/login details.
  - `Vehicle.java` – Manages registered vehicles.

## Features

- Vehicle registration (with license plate and type).
- Slot booking with start/end time.
- Payment handling (Paid/Pending).
- Reports generation for users.
- Input validation using annotations.

##  Technologies

- **Java 17+**
- **Spring Boot**
- **Spring Data JPA (Hibernate)**
- **MySQL/PostgreSQL** (configurable)
- **Lombok** (for reducing boilerplate)
- **Jakarta Persistence API**

##  Database Schema

All tables are created under schema:
