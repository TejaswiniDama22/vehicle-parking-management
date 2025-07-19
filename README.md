1. Exception Handling (cfg.lms.exception)
    We implemented a global exception handling mechanism using @ControllerAdvice to ensure consistent error responses across the application.
    
    Custom Exceptions:
    UserAlreadyExistsException
    Thrown when a user attempts to register with an email that already exists in the system.
    
    BookingConflictException
    Thrown when a booking can't be completed due to issues like time overlap or unavailable slots.
    
    GlobalExceptionHandler:
    This class centralizes error handling for different exception types:
    
    Validation Errors (MethodArgumentNotValidException) – returns a BAD_REQUEST with a custom error message.
    
    Custom Exceptions (UserAlreadyExistsException, BookingConflictException) – returns specific messages with appropriate HTTP statuses like 409 CONFLICT.
    
    Illegal Inputs (IllegalArgumentException) – handles invalid vehicle types, null users, etc.
    
    General Exception Handler – catches any unexpected exceptions and returns a 500 error.
    
    This setup ensures user-friendly error responses and clean code separation.
    
2. Booking Service (BookingService)
The BookingService handles parking slot booking with time and slot validation.

Key Features:
     Time Range Validation: Ensures end time is after start time.
    
     User Booking Conflict Check: Prevents overlapping bookings for the same user.
    
     Slot Availability Check: Limits bookings to maxSlots = 10.
    
     Parking Slot Allocation: Chooses the first available slot or creates one (fallback).
    
     Vehicle Validation: Checks if the vehicle with the given license plate exists.
    
     Booking Creation: Generates a unique bookingId, associates user, vehicle, time, and slot.
    
     Fare Calculation: Calculates cost based on duration and vehicle type:

  CAR: ₹50/hour
  
  BIKE: ₹30/hour
  
  Response:
  Returns a ResponseData object with status, message, and a BookingSummary (booking ID, type, hours, and fare).

3. Payment Service (PaymentService)
    This service is responsible for calculating the fare after a booking is made.
    
    Uses booking's start and end time to calculate duration.
    
    Applies hourly rates based on vehicle type (CAR or BIKE).
    
    Ensures a minimum charge of 1 hour even if time difference is less.

4. User Registration (UserService)
    Handles new user registration with validation and uniqueness check.
    
    Workflow:
    Checks if the email is already registered using userRepository.findByEmail.
    
    Generates a unique 4-digit user ID using random numbers.
    
    Saves the user to the database using userRepository.save.
    
    Returns a success ResponseData with user details.
   
Response Example:
   {
  "status": "SUCCESS",
  "message": "User registered successfully with User ID: 5001",
  "data": {
    "userId": 5001,
    "name": "Harsh",
    "email": "harsh@gmail.com"
    }
   }
