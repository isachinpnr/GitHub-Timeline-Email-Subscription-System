# GitHub Timeline Email Subscription System

A pure PHP-based email subscription system that allows users to register for GitHub timeline updates, verify their email with a 6-digit code, and unsubscribe securely. Built without external dependencies, following rtCamp's assignment guidelines, using PHP, HTML, CSS, and Mailtrap for email testing.

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Setup Instructions](#setup-instructions)
- [Project Workflow](#project-workflow)
- [File Structure](#file-structure)
- [rtCamp Guidelines Compliance](#rtcamp-guidelines-compliance)
- [Challenges and Solutions](#challenges-and-solutions)
- [Testing](#testing)
- [License](#license);

## Demo Video
Watch a quick demo of the project - https://youtu.be/xu7P5X8AfG4?si=11RGNBFWQjW02jCg  
<!-- *Note*: The video is private; contact the author for access if needed. -->

## Project Overview
This project is a web application that lets users subscribe to receive periodic GitHub timeline updates (e.g., Linus Torvalds' public activity) via email. Users register their email, verify it using a 6-digit code sent to their inbox, and can unsubscribe anytime with a similar verification process. Updates are sent every 5 minutes via a CRON job, fetching data from a GitHub Atom feed and formatting it into an HTML table. Emails are stored in a text file, and the system uses Mailtrap for testing email delivery.

The project is built with pure PHP, HTML, and CSS, ensuring no external libraries or frameworks, as per rtCamp's requirements. It’s designed to be simple, scalable, and secure, with clean UI and robust error handling.

## Features
- **Email Registration**: Users submit an email, receive a 6-digit verification code, and verify to subscribe.
- **Unsubscription**: Secure unsubscribe process with email and code verification.
- **GitHub Timeline Updates**: Fetches public GitHub activity (e.g., `torvalds.atom`) and sends formatted HTML updates every 5 minutes.
- **Email Storage**: Subscribed emails are stored in `registered_emails.txt` with case-insensitive duplicate checks.
- **Clean UI**: Responsive forms with modern styling (blue for subscribe, red for unsubscribe).
- **Error Handling**: Success/error pop-ups, logging for debugging, and secure file operations.
- **Mailtrap Integration**: Uses Mailtrap SMTP for testing email delivery.

## Tech Stack
- **Backend**: PHP 8.3 (no frameworks)
- **Frontend**: HTML, CSS (pure, no libraries)
- **Email Testing**: Mailtrap SMTP
- **Storage**: Plain text file (`registered_emails.txt`)
- **CRON Job**: Linux CRON for scheduling updates
- **Server**: XAMPP (Apache + PHP)

## Setup Instructions
Follow these steps to set up and run the project locally.

### Prerequisites
- XAMPP (or any Apache/PHP server) with PHP 8.4+
- Mailtrap account for SMTP testing
- Linux environment (e.g., Kali Linux) for CRON setup
- Git (optional for cloning repo)

### Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/github-timeline-isachinpnr.git
   cd github-timeline-isachinpnr/src

### Project Workflow
The project follows a clear workflow for user interaction and backend processing.

1. Email Registration (index.php):
User submits email → PHP generates a 6-digit code → Stores email and code in session → Sends code via Mailtrap → Shows "Verification code sent" pop-up.

User enters code → PHP verifies code against session → Saves email to registered_emails.txt → Shows "Email registered successfully" or "Email already registered" pop-up.

2. GitHub Timeline Updates (functions.php + CRON):
CRON job runs sendGitHubUpdatesToSubscribers() every 5 minutes.

Fetches GitHub Atom feed (e.g., torvalds.atom) → Parses XML → Formats into HTML table → Sends to all emails in registered_emails.txt with unsubscribe link.

3. Unsubscription (unsubscribe.php):
User submits email → PHP generates and sends a new 6-digit code → Shows "Unsubscribe code sent" pop-up.

User verifies code → PHP removes email from registered_emails.txt → Shows "You are unsubscribed" or "Email not found" pop-up.

4. Storage & Security:
Emails stored in registered_emails.txt with case-insensitive duplicate checks.

Session-based verification ensures secure registration/unsubscription.

File locking (LOCK_EX) prevents race conditions during file writes.

5. UI & Feedback:
Responsive forms styled with pure CSS (blue for subscribe, red for unsubscribe).

Success (green) and error (red) pop-ups provide clear user feedback.

Logging (error_log()) tracks email sending for debugging.

### File Structure

github-timeline-isachinpnr/
├── README.md               # Project documentation
└── src/
    ├── index.php           # Registration and verification page
    ├── unsubscribe.php     # Unsubscription page
    ├── functions.php       # Core logic (email, GitHub API, file handling)
    ├── cron.php            # CRON script for periodic updates
    ├── setup_cron.sh       # Script to set up CRON job
    └── registered_emails.txt # Stores subscribed emails

## rtCamp Guidelines Compliance

This project adheres to rtCamp's assignment requirements:
1. Pure PHP: No frameworks or libraries used, only built-in PHP functions (mail(), simplexml_load_string(), etc.).

2. No Dependencies: Entirely self-contained, using plain PHP, HTML, and CSS.

3. Mailtrap for Testing: Emails sent via Mailtrap SMTP to avoid real email delivery.

4. Clean Code: Well-structured, commented, and maintainable code.

5. Responsive UI: CSS ensures forms are user-friendly on desktop and mobile.

6. Secure: Session-based verification, file locking, and proper permissions.

## License
This project is for rtCamp assignment purposes and is not licensed for public use. Contact the author for permissions.

# Author: Sachin Panwar
# GitHub: @isachinpnr
# Email:  uttarakhandtechnology@gmail.com


