# Bus Station Management System

This is a bus station management program written in C. We made it for a practical work at university. It runs in the terminal and keeps all the departures in a singly linked list.

## What it does

You can add, delete and modify departures (only the time can be changed), search by destination, reserve seats, cancel reservations and get a refund, and see the list of departures (normal order or sorted by time). There is also a statistics page with the number of departures, tickets sold and total revenue.

## Rules we followed

- Every departure has its own number, so two departures can't have the same one.
- A departure stores: destination, time, bus capacity, available seats, ticket price, revenue and number of tickets sold.
- There are three kinds of passengers: adult (full price), student (20% off) and child (50% off).
- Reserving a seat lowers the available seats and raises the number of tickets sold and the revenue.
- Cancelling gives the seat back and the revenue is updated.

## Files

- `main.c`: the main menu and the flow of the program
- `Display.c`: display, search, statistics and sorting
- `DATABASE.C`: adding, modifying and deleting departures
- `Reservation.c`: reservations, cancellations, prices and discounts
- `Exist.c`: checks if a departure exists
- `Exit.c`: asks for confirmation before leaving and frees the memory
- `datastructure.h`: the structures and the function declarations
- `Makefile.win`: build file for Windows (MinGW)
- `BUS STATION MANAGEMENT.exe`: the compiled version for Windows

## Data structure

Each departure is stored in a node of a linked list:

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

## How to build

You need a C compiler like GCC or MinGW. In the project folder run:

```bash
gcc -std=c11 main.c Display.c DATABASE.C Exist.c Exit.c Reservation.c -o "BUS STATION MANAGEMENT"
```

and then:

```bash
./"BUS STATION MANAGEMENT"
```

On Windows you can also use the Makefile:

```bash
mingw32-make -f Makefile.win
```

and run `BUS STATION MANAGEMENT.exe`.

## How to use it

When you start the program you get a menu:

1. Add departure
2. Delete departure
3. Modify departure time
4. Search by destination
5. Reserve a seat
6. Cancel reservation
7. Display departures
8. Display departures by time
9. Display statistics
10. Exit

You type the number of the option you want. The program asks you to confirm before it goes on, and everything is entered with the keyboard (mostly integers).

A normal test goes like this: add a departure, reserve a seat with its number, pick the passenger type, look at the list or the statistics, cancel the reservation if you want, then exit. The memory is freed when you leave.
