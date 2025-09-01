# Airbnb Clone — Technical and Functional Requirements

**Repository:** `alx-airbnb-project-documentation`  
**File:** `requirements.md`

---

## 1. User Authentication

**Description:**  
Handles user registration, login, and profile management for guests, hosts, and admins.

**API Endpoints:**
| Method | Endpoint             | Description                         |
|--------|--------------------|-------------------------------------|
| POST   | /api/auth/register | Register a new user                  |
| POST   | /api/auth/login    | Login existing user                  |
| GET    | /api/auth/profile  | Retrieve user profile                |
| PUT    | /api/auth/profile  | Update user profile                  |

**Input/Output Specifications:**
- **Registration Input:**  
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "password": "Password123!",
  "role": "guest"
}
Login Input:


{
  "email": "john@example.com",
  "password": "Password123!"
}
Output: JWT token for authentication, user details on success.

Validation Rules:

Email must be unique and valid format.

Password must have at least 8 characters, including letters and numbers.

Role must be one of guest, host, admin.

Performance Criteria:

Registration and login response time < 500ms.

JWT tokens expire after 1 hour for security.

2. Property Management
Description:
Allows hosts to create, update, and delete property listings.

API Endpoints:

Method	Endpoint	Description
POST	/api/properties	Create a new property listing
GET	/api/properties	List all properties
GET	/api/properties/:id	Get property details
PUT	/api/properties/:id	Update property details
DELETE	/api/properties/:id	Delete a property listing

Input/Output Specifications:

Create Property Input:


{
  "host_id": "uuid-of-host",
  "name": "Cozy Apartment",
  "description": "2-bedroom apartment in city center",
  "location": "New York, NY",
  "price_per_night": 120.50
}
Output: Property object with unique property_id.

Validation Rules:

name, description, location, price_per_night are required.

price_per_night must be a positive decimal.

Performance Criteria:

Property retrieval (GET) < 300ms for single property.

Creation, update, and deletion < 500ms.

3. Booking System
Description:
Handles property bookings, cancellations, and tracks booking status.

API Endpoints:

Method	Endpoint	Description
POST	/api/bookings	Create a new booking
GET	/api/bookings	List all bookings
GET	/api/bookings/:id	Get booking details
PUT	/api/bookings/:id/cancel	Cancel a booking
GET	/api/bookings/user/:user_id	List bookings for a specific user

Input/Output Specifications:

Create Booking Input:


{
  "property_id": "uuid-of-property",
  "user_id": "uuid-of-user",
  "start_date": "2025-09-10",
  "end_date": "2025-09-15"
}
Output: Booking object with booking_id, total price, and status (pending by default).

Validation Rules:

Start date must be before end date.

Property must be available for the requested dates.

User must exist in the system.

Performance Criteria:

Booking creation response < 500ms.

System prevents double-booking for the same property and dates.
