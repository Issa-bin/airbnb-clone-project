## Entities and Attributes

### 1. User Entity
- user_id (PK)
- email
- password_hash
- first_name
- last_name
- phone_number
- created_at
- updated_at
- is_host (boolean)
- is_verified (boolean)

### 2. Property Entity
- property_id (PK)
- host_id (FK to User.user_id)
- title
- description
- address
- city
- state
- zip_code
- country
- latitude
- longitude
- property_type
- price_per_night
- max_guests
- bedrooms
- bathrooms
- amenities
- created_at
- updated_at
- is_available (boolean)

### 3. Booking Entity
- booking_id (PK)
- guest_id (FK to User.user_id)
- property_id (FK to Property.property_id)
- check_in_date
- check_out_date
- total_price
- number_of_guests
- booking_status (pending/confirmed/cancelled/completed)
- created_at
- updated_at
- payment_status

### 4. Review Entity
- review_id (PK)
- booking_id (FK to Booking.booking_id)
- reviewer_id (FK to User.user_id)
- reviewee_id (FK to User.user_id) OR property_id (FK to Property.property_id)
- rating (1-5)
- comment
- created_at

### 5. Payment Entity (Optional)
- payment_id (PK)
- booking_id (FK to Booking.booking_id)
- amount
- payment_method
- payment_status
- transaction_id
- payment_date

## Relationships

1. **User → Booking** (One-to-Many)
   - One user can have many bookings
   - A booking belongs to one user (guest)

2. **User → Property** (One-to-Many) 
   - One user (host) can have many properties
   - A property belongs to one user

3. **Property → Booking** (One-to-Many)
   - One property can have many bookings
   - A booking is for one property

4. **Booking → Review** (One-to-One or One-to-Many)
   - One booking can have one or two reviews (guest review and host review)

5. **User → Review** (One-to-Many)
   - One user can write many reviews
   - One user can receive many reviews