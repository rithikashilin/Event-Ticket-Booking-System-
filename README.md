# Event-Ticket-Booking-System-

Overview
  The Event Ticket Booking System is a command-line Python application built using SQLite3 for database management. The system enables users to sign up, log in, browse available events, book tickets, cancel bookings, and view their reservations. Administrators can manage events by adding, updating, deleting, and monitoring bookings.
  The application implements role-based access control, differentiating between Admin and User functionalities while maintaining event seat availability and booking integrity.

Features

User Features
  ~User registration with unique username validation
  ~Secure password setup with strength validation
  ~User login authentication
  ~View available events
  ~Book tickets for events
  ~Cancel booked tickets
  ~View personal booking history

Admin Features
  ~Admin login access
  ~Add new events
  ~Prevent duplicate event creation
  ~View all events
  ~Update event details
  ~Delete events without existing bookings
  ~View all user bookings
  ~Track event creator and editor

System Features
  ~SQLite database integration
  ~Foreign key relationships
  ~Automatic seat availability management
  ~Role-based dashboards
  ~Input validation and error handling
  ~Booking and cancellation tracking

Technology Stack
  ~Language: Python
  ~Database: SQLite3
  ~Modules Used:
     ~sqlite3
     ~re (Regular Expressions)

Database Design

Users Table
Column	    Type	         Description
User_id	    INTEGER (PK)	 Unique user ID
Username	  TEXT           UNIQUE	Username
Password	  TEXT	         User password
Role	      TEXT	         User role (Admin/User)

Events Table
Column	        Type	          Description
Event_id	      INTEGER (PK)	  Unique event ID
Event_name	    TEXT	          Event name
Event_date	    TEXT	          Event date
Venue	          TEXT	          Event location
Total_seats	    INTEGER	        Total number of seats
Available_seats	INTEGER	        Available seats
Event_addedby	  TEXT	          Event creator
Event_editedby	TEXT	          Last editor

Bookings Table
Column	      Type	        Description
Booking_id	  INTEGER (PK)	Unique booking ID
User_id	      INTEGER (FK)	User reference
Event_id	    INTEGER (FK)	Event reference
Tickets	      INTEGER	      Number of tickets booked

Default Admin Credentials

Username : Admin1
Password : Adminpass@123
These credentials are automatically inserted when the application starts for the first time.

Password Validation Rules
The system enforces strong password creation using Regular Expressions.
A valid password must contain:
  ~Minimum 8 characters
  ~At least one uppercase letter
  ~At least one lowercase letter
  ~At least one number
  ~At least one special character

Application Workflow

User Registration
  ~User selects Signup.
  ~Username uniqueness is verified.
  ~Password strength is validated.
  ~User account is created.

User Login
  ~Enter username and password.
  ~Credentials are validated.
  ~User is redirected to the appropriate dashboard.

Event Booking
  ~User views available events.
  ~Selects an Event ID.
  ~Enters ticket quantity.
  ~Booking is stored.
  ~Available seats are automatically reduced.

Ticket Cancellation
  ~User views bookings.
  ~Selects Booking ID.
  ~Booking is removed.
  ~Event seat count is restored.

Event Management (Admin)
  ~Add new events.
  ~View all events.
  ~Update event date.
  ~Delete events with no bookings.
  ~Monitor all bookings.

Project Structure

Event Ticket Booking System
│
├── event_booking.db
├── main.py
│
├── User Management
│   ├── setup_password()
│   ├── check_username()
│   └── login()
│
├── Event Management
│   ├── add_event()
│   ├── view_events()
│   └── update_events()
│
├── Booking Management
│   ├── book_ticket()
│   ├── cancel_bookings()
│   └── view_bookings()
│
├── Dashboards
│   ├── user_dashboard()
│   └── admin_dashboard()
│
└── main()

