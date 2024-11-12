# Gator Ticket Master System

A seat booking and management system for Gator Events implemented using Red-Black trees and Binary Min-Heaps.

## Project Structure
```
gator_ticket_master/
├── gatorTicketMaster.py    # Main program file
├── Makefile                # Build configuration
├── README.md               # This file
└── test1.txt               # Sample test file
```

## Requirements
- Python 3.7 or higher
- No external libraries required

## Installation

1. Clone or download the project:
```bash
git clone <repository-url>
cd gator_ticket_master
```

2. Make the program executable:
```bash
make
```

## Usage

### Running the Program
```bash
python3 gatorTicketMaster.py <input_file>.txt
```

### Input File Format
The input file should contain commands, one per line, in the following format:

```
Initialize(5)
Available()
Reserve(1, 1)
Cancel(1, 1)
```

### Supported Commands

1. `Initialize(seatCount)` 
   - Initialize system with specified number of seats
   - Example: `Initialize(5)`

2. `Available()`
   - Show available seats and waitlist length
   - Example: `Available()`

3. `Reserve(userID, userPriority)`
   - Reserve a seat for user with given priority
   - Example: `Reserve(1, 1)`

4. `Cancel(seatID, userID)`
   - Cancel reservation for specific seat and user
   - Example: `Cancel(1, 1)`

5. `ExitWaitlist(userID)`
   - Remove user from waitlist
   - Example: `ExitWaitlist(1)`

6. `UpdatePriority(userID, userPriority)`
   - Update priority of waitlisted user
   - Example: `UpdatePriority(1, 2)`

7. `AddSeats(count)`
   - Add new seats to the system
   - Example: `AddSeats(3)`

8. `PrintReservations()`
   - Print all current reservations
   - Example: `PrintReservations()`

9. `ReleaseSeats(userID1, userID2)`
   - Release seats for range of users
   - Example: `ReleaseSeats(1, 4)`

10. `Quit()`
    - End program execution
    - Example: `Quit()`

### Example Usage

1. Create a test input file (e.g., `test1.txt`):
```
Initialize(5)
Available()
Reserve(1, 1)
Reserve(2, 1)
Cancel(1, 1)
Reserve(3, 1)
PrintReservations()
Quit()
```

2. Run the program:
```bash
./gatorTicketMaster test1.txt
```

3. Check output file (`test1_output_file.txt`):
```
5 Seats are made available for reservation
Total Seats Available : 5, Waitlist : 0
User 1 reserved seat 1
User 2 reserved seat 2
User 1 canceled their reservation
User 3 reserved seat 1
[seat 1, user 3]
[seat 2, user 2]
Program Terminated!!
```

## Testing

1. Basic Test:
```bash
# Create test file
cat > test1.txt << EOL
Initialize(3)
Reserve(1, 1)
Reserve(2, 1)
Reserve(3, 1)
Reserve(4, 1)
Available()
Quit()
EOL

# Run test
python3 gatorTicketMaster.py test1.txt
```

2. Waitlist Test:
```bash
# Create test file
cat > test2.txt << EOL
Initialize(2)
Reserve(1, 1)
Reserve(2, 2)
Reserve(3, 3)
UpdatePriority(3, 1)
Cancel(1, 1)
PrintReservations()
Quit()
EOL

# Run test
python3 gatorTicketMaster.py test2.txt
```

## Error Handling

The system handles various error cases:
- Invalid input file
- Invalid command format
- Invalid seat numbers
- Invalid user IDs
- Invalid priorities
- Non-existent reservations

Error messages will be written to the output file.

## Cleanup

To clean generated files:
```bash
make clean
```

## Performance

- Most operations: O(log n) time complexity
- Memory usage: O(n) where n is number of seats
- Efficient handling of large numbers of reservations

## Limitations

- Single event support only
- No persistent storage
- No user authentication
- No concurrent access handling

## Author
[Durga Sritha Dongla (UFID:54220803)]

## License
This project is part of the Advanced Data Structures (COP 5536) course at the University of Florida.
