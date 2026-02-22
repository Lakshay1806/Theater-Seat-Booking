-- CREATE DATABASE
CREATE DATABASE IF NOT EXISTS theatre_db;
USE theatre_db;

-- 1. THEATER
CREATE TABLE theater (
    theater_id INT PRIMARY KEY AUTO_INCREMENT,
    theater_name VARCHAR(100) NOT NULL
);

-- 2. SCREEN
CREATE TABLE screen (
    screen_id INT PRIMARY KEY AUTO_INCREMENT,
    theater_id INT,
    total_seat INT,
    FOREIGN KEY (theater_id) REFERENCES theater(theater_id)
        ON DELETE CASCADE
);

-- 3. SEAT
CREATE TABLE seat (
    seat_id INT PRIMARY KEY AUTO_INCREMENT,
    screen_id INT,
    seat_type VARCHAR(20),
    accessibility BOOLEAN,
    FOREIGN KEY (screen_id) REFERENCES screen(screen_id)
        ON DELETE CASCADE
);

-- 4. MOVIE
CREATE TABLE movie (
    movie_id INT PRIMARY KEY AUTO_INCREMENT,
    movie_title VARCHAR(150),
    duration INT,
    language VARCHAR(30)
);

-- 5. SHOW
CREATE TABLE show_table (
    show_id INT PRIMARY KEY AUTO_INCREMENT,
    screen_id INT,
    movie_id INT,
    show_time DATETIME,
    FOREIGN KEY (screen_id) REFERENCES screen(screen_id)
        ON DELETE CASCADE,
    FOREIGN KEY (movie_id) REFERENCES movie(movie_id)
        ON DELETE CASCADE
);

-- 6. CUSTOMER
CREATE TABLE customer (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100),
    email VARCHAR(100),
    phone_number VARCHAR(15)
);

-- 7. BOOKING
CREATE TABLE booking (
    booking_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    show_id INT,
    FOREIGN KEY (customer_id) REFERENCES customer(customer_id)
        ON DELETE CASCADE,
    FOREIGN KEY (show_id) REFERENCES show_table(show_id)
        ON DELETE CASCADE
);

-- 8. BOOKED_SEAT (Prevents double booking)
CREATE TABLE booked_seat (
    booking_id INT,
    seat_id INT,
    show_id INT,
    price_paid DECIMAL(8,2),

    PRIMARY KEY (seat_id, show_id),

    FOREIGN KEY (booking_id) REFERENCES booking(booking_id)
        ON DELETE CASCADE,
    FOREIGN KEY (seat_id) REFERENCES seat(seat_id)
        ON DELETE CASCADE,
    FOREIGN KEY (show_id) REFERENCES show_table(show_id)
        ON DELETE CASCADE
);
