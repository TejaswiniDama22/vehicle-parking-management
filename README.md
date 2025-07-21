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
#### Validations:
 Name:
Required – must not be empty.

📧 Email:
Must be valid and end with .com or .in (e.g., example@gmail.com).

🔒 Password:
Must be at least 8 characters long.


### VEHICLE_REGISTRATION

**Method:** POST  
**URL:** http://localhost:8080/vehicle/register  
**Content-Type:** application/json

#### Request Body
```
json
{
  "userId": 9641,
  "licensePlate": "JH12AB9634",
  "vehicleType": "CAR"
}


```
### Validations:

🆔 User ID is required and must exist in the system.

🔢 License Plate must follow the format: JH12AB963
(2 uppercase letters + 2 digits + 2 uppercase letters + 4 digits).

🚙 Vehicle Type must be either CAR or BIKE .


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
  "licensePlate": "JH12AB9634",
  "start": "2025-07-18T14:00:00",
  "end": "2025-07-18T16:00:00"
}
```

### Validations:
🆔 userId:
Must not be null and should refer to a valid, existing user.

🚗 vehicleType:
Required – must be either CAR or BIKE (case-sensitive).

🔖 licensePlate:
Required – must match a previously registered vehicle.

⏰ start / end:
Both must be future timestamps, i.e., later than the current system time.

