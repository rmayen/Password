# Advanced Password Generator

A Java command-line tool that generates cryptographically secure random passwords with configurable composition rules.

## Overview

The program prompts the user for a total password length and minimum required counts of uppercase letters, lowercase letters, digits, and special characters. It then generates a password that satisfies those constraints, fills the remaining length from the full character pool, and shuffles the result so the required characters aren't clumped at the start.

## Purpose

Built to practice secure random number generation, custom exceptions, and input validation in Java — and to produce passwords strong enough to actually use.

## Technologies Used

- Java (JDK 8+)
- `java.security.SecureRandom` for cryptographically strong randomness
- `java.util.Scanner` for interactive input

## Features

- Configurable total length
- Minimum-count rules per character category (upper, lower, digits, special)
- Custom `InsufficientLengthException` when minimums exceed total length
- Fisher–Yates shuffle so required characters land at random positions
- Uses `SecureRandom` rather than `Math.random()` for security-sensitive output

## Setup / Run

Requires a JDK (8 or newer) installed.

```bash
git clone https://github.com/rmayen/Password.git
cd Password
javac AdvancedPasswordGenerator.java
java AdvancedPasswordGenerator
```

Then follow the prompts.

### Example

```
Enter the desired total length for your password: 16
Minimum number of uppercase letters: 2
Minimum number of lowercase letters: 2
Minimum number of digits: 2
Minimum number of special characters: 2
Generated Password: k#9Qm2!pLx7@vRnA
```

## Project Structure

```
Password/
└── AdvancedPasswordGenerator.java   # Entry point and generator logic
```

## My Role

I designed and implemented the full program: the generation algorithm, the custom exception for invalid input, the shuffle step, and the interactive CLI.

## Lessons Learned

- Why `SecureRandom` matters for anything password-related versus `Math.random()` or plain `Random`.
- Implementing a custom checked exception to signal a domain-specific error (required minimums exceed length).
- Using Fisher–Yates to get an unbiased shuffle so the required-character slots don't leak structure.
