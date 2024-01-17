# HMAC-based One-Time Password (HOTP) Generator Overview

---
# Introduction
## What is HOTP?
HMAC-based one-time password(HOTP, RFC 4226)  is a method of generating one-time passwords that are valid for a single login session or transaction, enhancing security by requiring a dynamic code in addition to a static password.

## Components of HOTP
1. ### Secret Key
   The secret key is a shared, secret value known to both the server and the user's device.
   It is used as input to the HMAC algorithm, ensuring that the generated codes are unique to the specific secret key.
2. ### Counter
   The counter is a numerical value that increments with each login attempt or transaction.
   It provides variability to the generated codes, ensuring that each code is unique to a specific counter value.
3. ### HMAC (Hash-based Message Authentication Code)
   HMAC is a cryptographic hash function that takes a secret key and input data to produce a fixed-size hash value.
   In HOTP, HMAC is used to generate a hash from the secret key and counter, producing a unique code for each counter value.
4. ### One-Time Password (OTP)
   The one-time password is the result of the HOTP algorithm, (eg. sequence of number).
   Purpose: It is the dynamic element used in two-factor authentication, valid for a single use or a short period.
   HOTP Workflow
   Initialization:

The server and the user's device share a secret key.
## User Authentication Request:

The user initiates an authentication request.
The server maintains a counter or timestamp associated with the user.
## HMAC Generation:

The server combines the secret key and the counter to generate an HMAC.
Code Extraction:

A portion of the HMAC output is extracted to create the one-time password.
## User Input:

The user enters the one-time password along with their static password.
## Verification:

The server repeats the HMAC generation process and compares the generated code with the user-provided code.
If they match, the user is authenticated.
