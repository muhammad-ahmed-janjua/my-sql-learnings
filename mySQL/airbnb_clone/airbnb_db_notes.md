## SQL Commands with Examples for the Airbnb-Style Database Schema

### 1. **SELECT** – Retrieve data from tables
   - Retrieve all users:
     ```sql
     SELECT * FROM users;
     ```
   - Retrieve specific columns for rooms:
     ```sql
     SELECT id, price, room_type, total_bedrooms FROM rooms;
     ```

### 2. **INSERT** – Add new data to tables
   - Add a new user:
     ```sql
     INSERT INTO users (email, bio, country)
     VALUES ('user@example.com', 'A frequent traveler', 'US');
     ```
   - Add a new room:
     ```sql
     INSERT INTO rooms (owner_id, price, hot_tub, home_type, room_type, total_occupancy, total_bedrooms, total_bathrooms, summary, latitude, longitude)
     VALUES (1, 150, true, 'Apartment', 'Private Room', 2, 1, 1, 'A cozy room in the heart of the city', -33.8688, 151.2093);
     ```

### 3. **UPDATE** – Modify existing data
   - Update the bio of a specific user:
     ```sql
     UPDATE users
     SET bio = 'Adventure enthusiast and travel lover'
     WHERE id = 1;
     ```
   - Change the price of a room:
     ```sql
     UPDATE rooms
     SET price = 180
     WHERE id = 2;
     ```

### 4. **DELETE** – Remove data
   - Delete a user:
     ```sql
     DELETE FROM users
     WHERE id = 5;
     ```
   - Remove a room by ID:
     ```sql
     DELETE FROM rooms
     WHERE id = 3;
     ```

### 5. **JOIN** – Combine rows from two or more tables
   - List all bookings with user and room details:
     ```sql
     SELECT b.id, u.email AS guest_email, r.summary AS room_summary, b.start_date, b.end_date, b.total
     FROM bookings b
     JOIN users u ON b.guest_id = u.id
     JOIN rooms r ON b.room_id = r.id;
     ```

### 6. **WHERE** – Filter records
   - Find rooms with a price below 100:
     ```sql
     SELECT * FROM rooms
     WHERE price < 100;
     ```
   - Find bookings for a specific user:
     ```sql
     SELECT * FROM bookings
     WHERE guest_id = 1;
     ```

### 7. **ORDER BY** – Sort records
   - List rooms ordered by price (ascending):
     ```sql
     SELECT * FROM rooms
     ORDER BY price ASC;
     ```
   - List users in alphabetical order by email:
     ```sql
     SELECT * FROM users
     ORDER BY email ASC;
     ```

### 8. **GROUP BY** – Group rows sharing a property
   - Count rooms by room type:
     ```sql
     SELECT room_type, COUNT(*) AS total_rooms
     FROM rooms
     GROUP BY room_type;
     ```

### 9. **AGGREGATE FUNCTIONS** – Perform calculations on columns
   - Find the average price of rooms:
     ```sql
     SELECT AVG(price) AS average_price FROM rooms;
     ```
   - Calculate total earnings from bookings:
     ```sql
     SELECT SUM(total) AS total_earnings FROM bookings;
     ```

### 10. **LIMIT** – Limit the number of records
   - Get the top 5 most expensive rooms:
     ```sql
     SELECT * FROM rooms
     ORDER BY price DESC
     LIMIT 5;
     ```

### 11. **BETWEEN** – Filter within a range
   - Find bookings within a date range:
     ```sql
     SELECT * FROM bookings
     WHERE start_date BETWEEN '2024-01-01' AND '2024-12-31';
     ```

### 12. **LIKE** – Search with a pattern
   - Find users whose bio contains "travel":
     ```sql
     SELECT * FROM users
     WHERE bio LIKE '%travel%';
     ```

---