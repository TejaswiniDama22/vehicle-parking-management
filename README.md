# Vehicle Parking Management System

A Spring Boot web application to manage vehicle parking slots, bookings, payments, and reports.

---

## Project Overview

The system allows:
- User registration and vehicle management.
- Parking slot booking and prevention of overlapping bookings.
- Payment tracking.
- Reporting functionalities.

---

## Database Design (Apache Derby)

**Database Schema**: `VehicleManagement`

### Tables and Mappings:

| Table Name      | Entity Class   | Relationships / Mappings                          |
|-----------------|---------------|----------------------------------------------------|
| Vuser           | User.java     | - One-to-Many with `Vehicle`<br> - One-to-Many with `Booking`<br> - One-to-Many with `Report` |
| Vehicle         | Vehicle.java  | - Many-to-One with `User`<br> - One-to-Many with `Booking` |
| Booking         | Booking.java  | - Many-to-One with `User`<br> - Many-to-One with `Vehicle`<br> - Many-to-One with `ParkingSlot`<br> - One-to-One with `Payment` |
| ParkingSlot     | ParkingSlot.java | - One-to-Many with `Booking` |
| Payment         | Payment.java  | - One-to-One with `Booking` |
| Report          | Report.java   | - Many-to-One with `User` |

---

## Entity Mappings

- **User.java**
  - Primary Key: `userId`
  - Fields: `name`, `email`, `password`
  - Relationships:
    - One User → Many Vehicles
    - One User → Many Bookings
    - One User → Many Reports

- **Vehicle.java**
  - Primary Key: `vehicleId`
  - Fields: `licensePlate`, `type`
  - Relationships:
    - Many Vehicles → One User

- **Booking.java**
  - Primary Key: `bookingId`
  - Fields: `startTime`, `endTime`
  - Relationships:
    - Many Bookings → One User
    - Many Bookings → One Vehicle
    - Many Bookings → One ParkingSlot
    - One Booking → One Payment

- **ParkingSlot.java**
  - Primary Key: `slotId`
  - Fields: `type`, `status`

- **Payment.java**
  - Primary Key: `paymentId`
  - Fields: `amount`, `status`
  - Relationships:
    - One Payment → One Booking

- **Report.java**
  - Primary Key: `reportId`
  - Fields: `description`
  - Relationships:
    - Many Reports → One User

---

## Technologies Used

- **Java 17+**
- **Spring Boot**
- **Spring Data JPA (Hibernate)**
- **Apache Derby (Database)**
- **Lombok**
- **Maven**

---

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/TejaswiniDama22/vehicle-parking-management.git
