# PESU CGPA & Marks Studio

A single-file web application for calculating SGPA and CGPA, breaking down PESU-style assessment components (**ISA 1**, **ISA 2**, **Assignment**, **ESA**, and **Lab**), importing marks from PDFs or a PESU proxy endpoint, simulating target CGPAs, and syncing data across devices via **Firebase** (with optional **Google Sign-In** or **Sync Key**).

## Key Features

- **Multiple Marks & Grade Entry Modes:**
  - **ISA + ESA Formula Mode:** Calculates non-lab subject totals using `(ISA1 + ISA2) / 2 + Assignment + ESA / 2`, with support for theory + lab combinations.
  - **Direct Total Marks Mode:** Converts total marks (`0–100`) directly into grades (`S`, `A`, `B`, `C`, `D`, `E`, `F`) and grade points (`10` down to `0`).
  - **Direct Grade Point Mode:** Enter grades or grade points directly (including `Audit / Non-Credit` courses).
  - **PDF Upload & Parser:** Parses PESU result/grade-card PDFs locally in the browser using `PDF.js` without uploading files to external servers.
- **Semester & CGPA Analytics:**
  - Manage multiple semesters and switch between them with live **SGPA** and **CGPA** updates.
  - View a semester-by-semester breakdown table and equivalent percentage conversion (`CGPA × 10`, `(CGPA − 0.75) × 10`, `CGPA × 9.5`, or `(CGPA − 0.50) × 10`).
- **Target CGPA Simulator:** Calculate the required SGPA across upcoming credits to hit a target CGPA.
- **Cross-Device Sync & Backups:**
  - Saves data locally in `localStorage` for instant offline access.
  - Supports **Firebase Realtime Database** synchronization using either **Google Sign-In (Firebase Auth)** or a **Sync Key** + **Database URL**.
  - Includes **Export JSON** and **Import JSON** for manual backups and transfers.
- **PESU Academy Auto-Fetch Support:**
  - Includes a form for **SRN/PRN**, **Password**, and an optional **PESU API / Proxy Endpoint URL** (credentials are not persisted to `localStorage` or Firebase).

## Getting Started

### Run Locally
1. Save the application code as `index.html`.
2. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari).

### Host with GitHub Pages
1. Push `index.html` to the `main` branch of your GitHub repository.
2. Go to **Settings → Pages** in your repository.
3. Under **Build and deployment → Branch**, select **`main`** and **`/ (root)`**, then click **Save**.

## Firebase & Google Sign-In Setup

1. Create a project in the [Firebase Console](https://console.firebase.google.com/) and create a **Realtime Database**.
2. *(Optional for Google Sign-In)* Enable **Google** under **Authentication → Sign-in method** and register a **Web app** under **Project settings** to copy your Firebase Web Config JSON.
3. In the **Firebase & Google Sign-In Sync** card inside the app:
   - Paste your **Firebase Realtime Database URL** (for example, `https://<your-db>.firebaseio.com` or `https://<your-db>.firebasedatabase.app`).
   - Either sign in with **Google** or enter a **Sync Key**, then click **Save & Connect**.

## Notes on PESU Portal Fetch & Security

- Because browsers enforce CORS restrictions on static pages hosted on origins like GitHub Pages, direct browser requests to `pesuacademy.com` can be blocked unless routed through a backend/proxy endpoint.
- Keep your Firebase Realtime Database rules configured appropriately before storing sensitive data long-term.

## Tech Stack

- **HTML5, CSS3 & Vanilla JavaScript (ES Modules)**
- **Firebase JS SDK** (Authentication & Realtime Database REST sync)
- **PDF.js** (Client-side PDF text extraction)
