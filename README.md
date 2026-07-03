# QR Attendance System

A full-stack web application that automates attendance marking using QR code scanning from IITK ID cards. Built with Node.js, Express, and image-processing libraries for real-time QR decoding and attendance logging.

## Features

- **QR Code Scanning** — Upload an ID card image and decode embedded QR data instantly.
- **Automated Attendance Marking** — Extracts roll numbers via regex parsing and validates against a registered range.
- **Duplicate Prevention** — Server-side checks block re-marking attendance for an already-scanned student.
- **Attendance Report** — View a live HTML summary of all marked students.
- **CSV Export** — Download attendance records as a CSV file for offline analysis.

## Tech Stack

| Layer            | Technology            |
|-------------------|------------------------|
| Backend           | Node.js, Express.js   |
| File Upload       | Multer                |
| QR Decoding       | Jimp, jsQR             |
| Data Storage      | JSON (file-based)      |
| Frontend          | HTML, CSS              |

## How It Works

1. User uploads a photo of their ID card via the web interface.
2. The image is decoded using **jsQR** to extract the raw QR string.
3. **parser.js** extracts and validates the roll number using regex + range checks.
4. If valid and not already marked, the roll number and timestamp are saved to `attendance.json`.
5. Users can view a live report (`/report`) or export all records as CSV (`/export`).

## Setup & Installation

```bash
# Clone the repository
git clone <repo-url>
cd qr-attendance-system

# Install dependencies
npm install

# Start the server
node app.js
```

The app will run on **http://localhost:3000**.

## API Endpoints

| Method | Endpoint    | Description                          |
|--------|-------------|---------------------------------------|
| POST   | `/scan`     | Upload an ID card image to mark attendance |
| GET    | `/report`   | View HTML attendance summary          |
| GET    | `/export`   | Download attendance data as CSV        |

## Future Improvements

- Add a database (e.g., MongoDB/PostgreSQL) instead of JSON file storage
- Add authentication for report/export access
- Support real-time camera-based scanning instead of file upload
- Add unit tests for parser and attendance logic

## Author

**Prince** — [GitHub](https://github.com/PrinceHitwari)
