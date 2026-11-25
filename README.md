# Bus Station Management System

A simple C-based bus station management application designed to manage departures, reservations, cancellations, and statistics using a linked list data structure.

## Overview

This project is a console application for a bus station operator. It allows users to add bus departures, delete them, modify their schedules, search by destination, reserve seats, cancel reservations, and display departure and revenue statistics.

The program is implemented in plain C and uses a singly linked list to store all departures.

## Main Features

- Add new departures
- Delete existing departures
- Modify departure time
- Search departures by destination
- Reserve seats for passengers
- Cancel reservations and calculate refunds
- Display departures in different orders
- Display departures sorted by time
- Show station statistics such as number of departures, tickets sold, and revenue
- Exit the application safely

## Business Rules

- Each departure has a unique number.
- Each departure contains destination, time, capacity, available seats, ticket price, total revenue, and number of sold tickets.
- Passenger categories include:
  - Adult: 0% discount
  - Student: 20% discount
  - Child: 50% discount
- Reservation reduces available seats and increases sold counts.
- Cancellation restores seats and updates revenue accordingly.

## Project Structure

- `main.c` — Main menu and application flow
- `Display.c` — Display and search functions, statistics, sorting logic
- `DATABASE.C` — Departure creation, modification, and deletion logic
- `Reservation.c` — Reservation and cancellation logic, ticket pricing, discounts
- `Exist.c` — Checks whether a departure exists
- `Exit.c` — Exit confirmation and memory cleanup
- `datastructure.h` — Shared structures and function declarations
- `Makefile.win` — Build instructions for Windows/MinGW
- `BUS STATION MANAGEMENT.exe` — Compiled Windows executable

## Data Structure

The application uses a linked list of `Departure` records:

```c
typedef struct {
    int number;
    char destination[50];
    Time departureTime;
    int busCapacity;
    int availableSeats;
    float tickprice;
    float revenue;
    int nbsold;
} Departure;

typedef struct list {
    Departure value;
    struct list* next;
} list;
```

This structure stores all departure data in memory and allows fast insertion, deletion, and searching.

## Requirements

- C compiler (GCC/MinGW recommended)
- Windows environment if using the provided `.exe` or `Makefile.win`

## Build Instructions

### Using GCC on Windows or Linux

From the project folder, run:

```bash
gcc -std=c11 main.c Display.c DATABASE.C Exist.c Exit.c Reservation.c -o "BUS STATION MANAGEMENT"
```

Then execute:

```bash
./"BUS STATION MANAGEMENT"
```

### Using the provided Makefile (Windows)

```bash
mingw32-make -f Makefile.win
```

Then run the generated executable:

```bash
BUS STATION MANAGEMENT.exe
```

## How to Use

When the program starts, it displays a menu with the following options:

1. Add departure
2. Delete departure
3. Modify departure time
4. Search by destination
5. Reserve a seat
6. Cancel reservation
7. Display departures
8. Display departures by time
9. Display statistics
10. Exit the application

After choosing an option, the program asks for confirmation before continuing. Each task uses integer prompts and console input for easy interaction.

## Example Workflow

1. Add a departure with a unique number and destination.
2. Reserve a seat using the departure number.
3. Choose passenger category (Adult, Student, or Child).
4. View departure list or statistics.
5. Cancel a reservation if needed.
6. Exit safely when finished.

## Notes

- The project was built as an academic practical work and focuses on linked-list-based data management.
- The interface is text-based and intended for terminal use.
- Memory is freed when the user exits the program.

## License

This project is provided as a student learning exercise and is not currently associated with a formal open-source license.

## Authors

This bus station management application was developed by a university group working on a practical programming project.
