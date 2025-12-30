# 🏦 MoneyMatrix - Advanced Secure Banking System

**MoneyMatrix** is a robust, console-based banking simulation built in **C**. It goes beyond simple data storage by implementing advanced data structures (**Binary Search Trees**) for high-performance indexing and cybersecurity principles for data protection.

This project simulates a real-world core banking environment, featuring persistent file storage, role-based access control, and transaction auditing.

---

## 🌟 Key Features

### 👤 User Module
* **Secure Authentication:** Login using Account Number or Username.
* **Account Dashboard:** View personal details with **PII (Personal Identifiable Information) Masking** (e.g., `********1234`).
* **Financial Operations:**
    * **Deposit:** Add funds to the account.
    * **Withdraw:** Secure cash withdrawal with balance checks.
    * **Fund Transfer:** Transfer money to other users securely using Account Numbers.
* **Transaction History:** View a detailed, timestamped log of all deposits, withdrawals, and transfers.

### 🛡️ Admin Module
* **User Oversight:** View a formatted table of all active users in the system.
* **Account Management:** Perform "Soft Deletes" to deactivate accounts without losing transaction history.
* **Security Override:** Reset user passwords in case of account recovery.

---

## ⚙️ Technical Architecture

The system is built on a modular procedural C architecture using a **Flat-File Database** approach.

* **Persistence:** Data is not lost when the program closes.
    * `accounts.txt`: Stores user credentials, balances, and profile data.
    * `transactions.txt`: Appends every financial action for auditing.
* **UI:** Uses `windows.h` for a responsive console interface, featuring color-coded feedback (Green for success, Red for errors) and coordinate-based cursor positioning (`gotoxy`).

---

## 🧠 Algorithmic Efficiency (DAA)

A key highlight of MoneyMatrix is its optimization of search operations.

### The Problem
In a standard file-based system, finding a user (for login or transfer) requires reading the file line-by-line. This results in a time complexity of **$O(N)$**, which becomes slow as the user base grows.

### The Solution: Binary Search Tree (BST)
MoneyMatrix implements an **In-Memory Indexing System**:
1.  Upon startup, the system reads `accounts.txt`.
2.  It constructs a **BST** storing only the `Account Number` and the `Array Index`.
3.  **Search Operations:** When a user logs in or transfers money, the system searches the BST.

**Performance Impact:**
* **Search Complexity:** Reduced to O(\log N).
* **Memory Efficiency:** We do not store the full user record in the tree, only the mapping keys.

---

## 🔐 Security Implementation

This project implements core cybersecurity concepts to ensure data integrity and confidentiality.

### 1. Password Hashing (Salted)
Passwords are **never** stored in plain text.
* **Algorithm:** Custom hashing function combined with a cryptographic **Salt**.
* **Storage:** The system stores the computed hash. During login, the input is hashed and compared against the stored hash.

### 2. Data Loss Prevention (DLP)
* **Input Masking:** When typing passwords, characters are replaced with `*` to prevent shoulder-surfing.
* **Output Masking:** When displaying user details (Dashboard), sensitive fields like **Aadhar Number** and **Mobile Number** are partially masked (e.g., `1234********`).

### 3. Input Sanitization
* Uses `fgets` instead of `scanf` for strings to prevent **Buffer Overflow** attacks.
* Validates numeric inputs (Aadhar/Mobile) to prevent injection of invalid data types.

---

## 🛠 Installation & Usage

### Prerequisites
* **OS:** Windows (Required for UI libraries).
* **Compiler:** GCC (MinGW) or any standard C compiler.

### Step 1: Clone the Repository
git clone [https://github.com/your-username/moneymatrix.git](https://github.com/PundirP360112/MONEYMATRIX)
cd moneymatrix

Step 2: Compile
gcc main.c -o moneymatrix

Step 3: Run
./moneymatrix


🔑 Default Admin Credentials

Username: admin

Password: admin123


