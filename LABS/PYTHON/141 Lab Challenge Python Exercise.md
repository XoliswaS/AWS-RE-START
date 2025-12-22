# 🐍 Python Automation: Prime Number Generation & File I/O

## 🎯 Project Overview
In this challenge, **I developed a Python 3 script** to solve a computational math problem and automate the storage of results within a Linux environment. The project demonstrates my ability to implement efficient algorithms, manage file systems programmatically, and document technical paths for future automation.

---

## 🛠️ The Challenge Requirements
**I directed the script to perform the following tasks:**
1.  **Calculate** every prime number between 1 and 250.
2.  **Automate** the creation of a `results.txt` file.
3.  **Export** the calculated primes into the text file for verification.
4.  **Validate** the script’s performance within a dual-version (Python 2/3) Linux environment.

---

## 📑 Step-by-Step Implementation

### Phase 1: Algorithmic Logic Design
**I architected the prime detection logic** focusing on mathematical efficiency. Instead of checking every possible divisor, I optimized the inner loop to stop at the square root of the number, significantly reducing CPU cycles.



### Phase 2: File Handling & Automation
To ensure the data persisted outside of the terminal, **I implemented a context manager** (`with open`) to handle the file stream. This ensures that even if the script encounters an error, the file is closed safely and resources are released.

### Phase 3: Environment Execution
Given that the Linux host contained both Python 2 and 3, **I specifically targeted the Python 3 interpreter** to ensure the use of modern syntax and better performance.

---

## 💻 The Solution Code

```python
# File: prime_generator.py
# Purpose: Calculate primes 1-250 and save to results.txt

def is_prime(n):
    """Evaluates if a number is prime using optimized divisor checking."""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# I used list comprehension for clean, readable data collection
primes = [str(num) for num in range(1, 251) if is_prime(num)]

# Automated File I/O
with open('results.txt', 'w') as f:
    f.write('\n'.join(primes))

print(f"Success: Found {len(primes)} primes and saved them to results.txt")
 
