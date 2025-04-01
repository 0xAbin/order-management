# Deribit Trading System

## Overview

The **Deribit Trading System**

### Features:
- Place Order
- Cancel Order
- Modify Order
- Get Orderbook
- View Current Positions
- WebSocket server for continuous orderbook updates

### Technologies:
- C++
- Boost
- OpenSSL
- WebSockets

---

## Installation

### Prerequisites:

Make sure the following dependencies are installed on your system:
- **CMake**: Version 3.10 or later
- **Boost**: Version 1.87 or later
- **OpenSSL**: Version 3.4.1 or later

You can install the necessary dependencies using **Homebrew** on macOS:

```bash
brew install cmake boost openssl
```

---

### Building the Project

1. Clone the repository:

```bash
git clone https://your-repository-url.git
cd order-management
```

2. Create a build directory and navigate into it:

```bash
mkdir build
cd build
```

3. Run `cmake` to configure the project:

```bash
cmake ..
```

4. Build the project using `make`:

```bash
make
```

---

## Running the Program

Once the build is complete, you can run the executable:

```bash
./bin/DeribitTradingSystem
```

This will start the Deribit Trading System.

---

## Running Tests

If you'd like to run the tests, you can use the following command:

```bash
./test_main
```

---

## Notes

- If you encounter any issues during the build, make sure you have all required dependencies installed and check that your `Boost` and `OpenSSL` installation paths are correctly configured.
- This system uses WebSockets to send real-time orderbook updates. Ensure your WebSocket server is properly set up.

---

