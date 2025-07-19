# vehicle-parking-management

# USER-CONTROLLER

## API Endpoints

---

### USER_REGISTRATION

**Method:** POST  
**URL:** http://localhost:8080/user/register  
**Content-Type:** application/json

#### Request Body
```
json
{
  "name": "harsh",
  "email": "harshrajput@gmail.com",
  "password": "harsh1@124"
}
```
### VEHICLE_REGISTRATION

**Method:** POST  
**URL:** http://localhost:8080/vehicle/register  
**Content-Type:** application/json

#### Request Body
```
json
{
  "userId": 9641,
  "licensePlate": "Jh123442",
  "vehicleType": "CAR"
}

```
### BOOKING_SLOT

**Method:** POST  
**URL:** http://localhost:8080/booking/book  
**Content-Type:** application/json

#### Request Body
```
json
{
  "userId": 9641,
  "vehicleType": "CAR",  // or "BIKE"
  "licensePlate": "Jh123442",
  "start": "2025-07-18T14:00:00",
  "end": "2025-07-18T16:00:00"
}
```
### PAYMENT_METHOD

**Method:** POST  
**URL:** http://localhost:8080/payment/pay  
**Content-Type:** application/json

#### Request Body
```
json
{
  "bookingId": 1619,
  "amount": 100
}
```
### FEEDBACK_REPORTS

**Method:** POST  
**URL:** http://localhost:8080/report/submit  
**Content-Type:** application/json

#### Request Body
```
json
{
  "userId": 9641,
  "description": "Parking slot was occupied by another vehicle."
}

```

## ADMIN-CONTROLLER

---

### FETCH_ALL_USERS

**Method:** `GET`  
**URL:** `http://localhost:8080/admin/users`  
**Content-Type:** `application/json`

#### Description

Fetches a list of all registered users. Accessible only by admin.

### FETCH_ALL_VEHICLES

**Method:** `GET`  
**URL:** `http://localhost:8080/admin/vehicles`  
**Content-Type:** `application/json`

#### Description

Fetches all registered vehicles along with user details. This endpoint is restricted to admin access only.

### FETCH_ALL_SLOTS

**Method:** `GET`  
**URL:** `http://localhost:8080/admin/slots`  
**Content-Type:** `application/json`

#### Description

Fetches a list of all parking slots along with their type and current booking status. Only accessible by admin.

### FETCH_ALL_BOOKINGS

**Method:** `GET`  
**URL:** `http://localhost:8080/admin/bookings`  
**Content-Type:** `application/json`

#### Description

Retrieves a complete list of all bookings in the system, including details of users, vehicles, slots, and booking times. Admin access required.

### FETCH_ALL_PAYMENTS

**Method:** `GET`  
**URL:** `http://localhost:8080/admin/payments`  
**Content-Type:** `application/json`

#### Description

Retrieves a list of all payments made in the system, including associated booking, user, vehicle, and slot details. Only accessible by admin.

### FETCH_ALL_REPORTS

**Method:** `GET`  
**URL:** `http://localhost:8080/admin/reports`  
**Content-Type:** `application/json`

#### Description

Fetches all user-submitted feedback or issue reports. Each report is linked to the corresponding user. Admin access only.

### UPDATE_SLOT_STATUS

**Method:** `PUT`  
**URL:** `http://localhost:8080/admin/slot/{id}/status?status=AVAILABLE`  
**Content-Type:** `application/json`

#### Description

Updates the status of a parking slot. Replace `{id}` with the slot ID you want to update.  
The `status` query parameter can be set to values like `AVAILABLE`, `BOOKED`, or `MAINTENANCE`.

> Example:  
> `PUT http://localhost:8080/admin/slot/5252/status?status=AVAILABLE`

> **Note:** This endpoint is restricted to admin users only.

### DELETE_BOOKING

**Method:** `DELETE`  
**URL:** `http://localhost:8080/admin/booking/{id}`  
**Content-Type:** `application/json`

#### Description

Deletes a booking from the system. Replace `{id}` with the booking ID you want to delete.

> Example:  
> `DELETE http://localhost:8080/admin/booking/1619`

> **Important:** You must **delete the associated payment** before deleting a booking.  
> **Note:** This action is restricted to admin users only.
