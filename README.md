# Ola_Data_Analytics

# SQL Questions:
1. **Retrieve all successful bookings:**
2. **Find the average ride distance for each vehicle type:**
3. **Get the total number of cancelled rides by customers:**
4. **List the top 5 customers who booked the highest number of rides:**
5. **Get the number of rides cancelled by drivers due to personal and car-related issues:**
6. **Find the maximum and minimum driver ratings for Prime Sedan bookings:**
7. **Retrieve all rides where payment was made using UPI:**
8. **Find the average customer rating per vehicle type:**
9. **Calculate the total booking value of rides completed successfully:**
10. **List all incomplete rides along with the reason:**

# Power BI Questions:
1. **Ride Volume Over Time**
2. **Booking Status Breakdown**
3. **Top 5 Vehicle Types by Ride Distance**
4. **Average Customer Ratings by Vehicle Type**
5. **Cancelled Rides Reasons**
6. **Revenue by Payment Method**
7. **Top 5 Customers by Total Booking Value**
8. **Ride Distance Distribution Per Day**
9. **Driver Ratings Distribution**
10. **Customer vs. Driver Ratings**

#1. Retrieve all successful bookings:
```sql
Create view sucessful_bookings As
SELECT * FROM bookings
WHERE Booking_Status = 'Success';

SELECT * FROM successful_bookings;
```

#2. Find the average ride distance for each vehicle type:
```sql
Create View ride_distance_for_each_vehicle As
SELECT Vehicle_Type, AVG(Ride_Distance) AS avg_distance 
FROM bookings
GROUP BY Vehicle_Type;

SELECT * FROM ride_distance_for_each_vehicle;
```

#3. Get the total number of cancelled rides by customers:
```sql
Create View cancelled_rides_by_customers As
SELECT COUNT(*) AS bookings 
FROM bookings
WHERE Booking_Status = 'Canceled by Customer';

SELECT * FROM cancelled_rides_by_customers;
```

#4. List the top 5 customers who booked the highest number of rides:
```sql
Create View Top_5_Customers As
SELECT Customer_ID, COUNT(Booking_ID) AS total_rides
FROM bookings
GROUP BY Customer_ID
ORDER BY total_rides DESC
LIMIT 5;

SELECT * FROM Top_5_Customers;
```

#5. Get the number of rides cancelled by drivers due to personal and car-related issues:
```sql
Create View Rides_cancelled_by_Drivers_P_C_Issues As
SELECT COUNT(*) 
FROM bookings
WHERE Canceled_Rides_by_Driver = 'Personal & Car related issue';
```

#6. Find the maximum and minimum driver ratings for Prime Sedan bookings:
```sql
Create View Max_Min_Driver_Rating As
SELECT MAX(Driver_Ratings) AS max_rating, 
       MIN(Driver_Ratings) AS min_rating
FROM bookings 
WHERE Vehicle_Type = 'Prime Sedan';

SELECT * FROM Max_Min_Driver_Rating;
```

#7. Retrieve all rides where payment was made using UPI:
```sql
Create View UPI_Payment As
SELECT * FROM bookings
WHERE Payment_Method = 'UPI';

SELECT * FROM UPI_Payment;
```

#8. Find the average customer rating per vehicle type:
```sql
Create View AVG_Cust_Rating As
SELECT Vehicle_Type, AVG(Customer_Rating) AS avg_customer_rating
FROM bookings
GROUP BY Vehicle_Type;

SELECT * FROM AVG_Cust_Rating;
```

#9. Calculate the total booking value of rides completed successfully:
```sql
Create View total_successful_ride_value As
SELECT SUM(Booking_Value) AS total_successful_ride_value
FROM bookings
WHERE Booking_Status = 'Success';

SELECT * FROM total_successful_ride_value;
```

#10. List all incomplete rides along with the reason:
```sql
Create View Incomplete_Rides_Reason As
SELECT Booking_ID, Incomplete_Rides_Reason
FROM bookings
WHERE Incomplete_Rides = 'Yes';

SELECT * FROM Incomplete_Rides_Reason;
```

# For the PowereBI the Questions where divide into 5 views 

## 1. Overall
- Ride Volume Over Time
- Booking Status Breakdown

![Alttext](overall.png)

## 2. Vehicle Type
- Top 5 Vehicle Types by Ride Distance

  ![Alttext](vehicle_type.png)

## 3. Revenue
- Revenue by Payment Method
- Top 5 Customers by Total Booking Value
-  Ride Distance Distribution Per Day

  ![Alttext](Revenue.png)

## 4. Cancellation
- Cancelled Rides Reasons (Customer)
- Cancelled Rides Reasons (Drivers)

 ![Alttext](Calcelation.png)

## 5. Ratings
- Driver Ratings
- Customer Ratings

![Alttext](Ratings.png)

