# Backend Requirement Specifications

This document outlines the functional and technical requirements for key backend features of the Airbnb Clone project.

---

## 1. User Authentication

### 📌 Description
Handles user registration, login, and authentication.

### 🔗 Endpoints
- `POST /api/register`: Registers a new user.
- `POST /api/login`: Authenticates a user and returns a token.
- `GET /api/profile`: Fetches authenticated user details.

### 🔒 Validation Rules
- Email: Valid format, must be unique.
- Password: Minimum 8 characters, at least one number and special character.
- Token-based authentication using JWT.

### 📈 Performance Criteria
- Login response in under 1 second.
- Rate limiting to prevent brute-force login attacks.

---

## 2. Property Management

### 📌 Description
Allows hosts to manage property listings.

### 🔗 Endpoints
- `POST /api/properties/`: Create new listing.
- `GET /api/properties/`: Retrieve all properties.
- `PUT /api/properties/{id}/`: Update a listing.
- `DELETE /api/properties/{id}/`: Delete a listing.

### 🔒 Validation Rules
- `name`, `location`, and `price_per_night` are required.
- Host must be authenticated.

### 📈 Performance Criteria
- Return paginated data in < 2 seconds.
- Use indexed search for location and price filtering.

---

## 3. Booking System

### 📌 Description
Enables users to book available properties.

### 🔗 Endpoints
- `POST /api/bookings/`: Create new booking.
- `GET /api/bookings/`: Retrieve user’s bookings.
- `PUT /api/bookings/{id}/`: Modify existing booking.
- `DELETE /api/bookings/{id}/`: Cancel booking.

### 🔒 Validation Rules
- `start_date` < `end_date`, no overlapping bookings allowed.
- Property must be available during the date range.

### 📈 Performance Criteria
- Conflict check and creation within 2 seconds.
- Optimize queries with proper indexes on `start_date`, `property_id`.

---

