# Real-Time Stock Trading Engine

## Overview
This project implements a real-time stock trading engine that matches **Buy** and **Sell** orders based on predefined rules. The engine operates with **lock-free data structures** and supports concurrent order processing in a multi-threaded environment.

## Features
- **Supports 1,024 stock tickers**
- **Lock-free order book implementation** using linked lists
- **Multi-threaded execution** for simulating real-world stock trading
- **Efficient O(n) matching algorithm** for finding optimal Buy-Sell pairs

## Functions
### 1. `addOrder(type, ticker, quantity, price)`
This function adds a **Buy** or **Sell** order to the order book.
- **Parameters:**
  - `type`: Order Type (`'B'` for Buy, `'S'` for Sell)
  - `ticker`: Stock identifier (0-1023)
  - `quantity`: Number of stocks
  - `price`: Price per stock
- **Time Complexity:** O(1) (Inserts at the head of a linked list)

### 2. `matchOrder()`
This function matches **Buy** and **Sell** orders based on the following criteria:
- A **Buy order** is matched if its price is **greater than or equal** to the **lowest available Sell price**.
- A **Sell order** is matched if its price is **less than or equal** to the **highest available Buy price**.
- **Order deactivation** is handled atomically to ensure thread safety.
- **Time Complexity:** O(n)

### 3. **Thread-Safe Execution**
- **Race conditions** are prevented using atomic operations.
- No locks are used to ensure **high performance** and **scalability**.

## Constraints
- **No use of dictionaries, maps, or equivalent data structures.**
- No language-specific imports providing pre-built data structures.
- The entire solution is implemented using **arrays and linked lists**.

## Implementation Approach
- Implemented in **C++** for precise memory and concurrency control.
- Uses **atomic pointers** for safe concurrent modifications.
- Uses **multiple threads** to simulate real-world stock trading.

## How to Run
1. Compile the C++ program using a compiler such as `g++`.
   ```sh
   g++ stock_trading.cpp -o stock_trading -pthread
   ```
2. Run the compiled executable:
   ```sh
   ./stock_trading
   ```

## Expected Output
- The program will generate random **Buy** and **Sell** orders.
- Matched orders will be displayed in the format:
  ```
  Matched: Buy Order (Ticker 512) at Price: 450
  Matched: Sell Order (Ticker 76) at Price: 300
  ```

## Future Enhancements
- Implement **priority queues** for faster order matching.
- Add **support for partial order execution**.
- Extend to handle **market vs. limit orders**.

---


