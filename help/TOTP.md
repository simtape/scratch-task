# Time-based One-Time Password (TOTP) Generator Overview

---
# Introduction
## What is TOTP?
TOTP is a method of generating one-time passwords that are valid for a specific time period, typically 30 seconds. It combines the security of HMAC (Hash-based Message Authentication Code) with a timestamp to create unique, time-sensitive codes.

## Components of TOTP
1. ### Secret Key 
   Similar to HOTP, the secret key is a shared, secret value known to both the server and the user's device. 
   It is used as input to the HMAC algorithm, ensuring the generated codes are unique to the specific secret key.
2. ### Timestamp
   The timestamp represents the current time, usually in 30-second intervals.
   It provides variability to the generated codes, ensuring that each code is unique to a specific time period.
3. ### HMAC (Hash-based Message Authentication Code)
   HMAC is a cryptographic hash function that takes a secret key and input data to produce a fixed-size hash value.
   In TOTP, HMAC is used to generate a hash from the secret key and timestamp, producing a unique code for each time period.
4. ### One-Time Password (OTP)
   The one-time password is the output of the TOTP algorithm, typically a numeric code.
   It is the dynamic element used in two-factor authentication, valid for a single use during a specific time window.
   TOTP Workflow
   Initialization:

The server and the user's device share a secret key.
## User Authentication Request:

The user initiates an authentication request.
The server uses the current timestamp to generate an OTP.
## HMAC Generation:

The server combines the secret key and the current timestamp to generate an HMAC.
## Code Extraction:

A portion of the HMAC output is extracted to create the one-time password.
## User Input:

The user enters the one-time password along with their static password.
## Verification:

The server repeats the HMAC generation process using the current timestamp and compares the generated code with the user-provided code.
If they match, and the timestamp is within an acceptable window, the user is authenticated.