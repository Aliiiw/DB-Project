# DB-Project

DB-Project is a Java database course project for a travel ticket reservation system inspired by services like Alibaba. The application uses Swing dialogs for the user interface and PostgreSQL/JDBC for data storage and queries.

The system supports multiple user roles, ticket reservation and purchase flows, travel management, discounts, reports, ratings, and a simple support messaging flow between users and the super admin.

## Features

- Swing-based desktop UI using `JOptionPane` dialogs.
- PostgreSQL integration through JDBC prepared statements.
- Role-based panels for Passenger, Agent, and Super Admin users.
- User sign-up and login with email or phone number.
- OTP verification flow for newly created users.
- Password encryption/decryption with Jasypt.
- Passenger ticket search for domestic flights, international flights, trains, and buses.
- Filtering by origin, destination, price range, date range, and agency rate.
- Ticket reservation, purchase, cancellation, and travel rating.
- Discount/offer creation and passenger assignment by Super Admin.
- Agent travel creation with vehicle type, origin, destination, date, capacity, and price.
- Agent reporting for ticket filters, income, cheapest/most expensive travel, popular destinations, travel ratings, and top passengers.
- Support-ticket style messaging between passengers/agents and Super Admin.
- Automatic travel status update for past travel dates.

## Main Roles

### Passenger

Passengers can search for available travels, reserve tickets, buy reserved tickets, view purchased tickets, cancel eligible tickets, rate completed travels, edit their profile, and message the Super Admin.

### Agent

Agents can create new travels, view and filter agency tickets, inspect travel rating reports, calculate income, find popular destinations, and view top passenger statistics.

### Super Admin

The Super Admin can create discount offers for passengers, view incoming messages, reply to users, and inspect chat history.

## Tech Stack

- Java
- Swing / JOptionPane
- PostgreSQL JDBC Driver
- Jasypt
- JavaMail / Activation
- IntelliJ IDEA project structure

## Project Structure

```text
src/
├── Main.java           # Application entry point and travel-status updater
├── Human.java          # Main user model plus role panels and database operations
├── SendEmail.java      # Email helper for OTP delivery
├── Role.java           # SUPERADMIN, PASSENGER, AGENT
├── Vehicle.java        # Airplane, Bus, Train
├── TicketStatus.java   # Reserve, Paid, Done, Cancelled
├── TravelStatus.java   # Done, NotDone
└── OfferStatus.java    # Used, NotUsed
```

## Database Expectations

The code expects a PostgreSQL database with tables such as:

- `human`
- `human_otp`
- `city`
- `travel`
- `ticket`
- `passenger_ticket`
- `agency`
- `agency_travel`
- `agency_admin`
- `offer`
- `offer_passenger`
- `support_ticket`
- `chat`

The repository does not currently include schema migration files, so the database schema must be created separately with fields matching the SQL queries in `Human.java` and `Main.java`.

## Required Libraries

The IntelliJ module file references these external JARs:

- PostgreSQL JDBC driver
- Jasypt
- JavaMail
- Activation

Add these libraries to the project/module classpath before running the app.

## Running the Project

1. Open the project in IntelliJ IDEA.
2. Add the required external JAR files to the module classpath.
3. Make sure the PostgreSQL schema exists and is reachable.
4. Review the database and mail configuration in the source before running.
5. Run `Main.java`.

## Security Notes

The current educational version keeps database and email configuration directly in the source code. Before using this beyond a local/course environment, move those values to environment variables or a private configuration file and rotate any credentials that were committed.

## Notes

This is a database-course style project focused on practicing SQL queries, JDBC, user roles, and reservation workflows. It is not production-ready and does not include a packaged build system such as Maven or Gradle.
