# XUMM + XRPL Flask Application

This is the server application for dCloud, python 3.9 or later is required!

- Connect their XRP Ledger wallet via XUMM SignIn  
- View their XRP balance  
- Manage trustlines (adding or listing tokens)  
- Create offers (trades) on the XRP Ledger  

## Table of Contents

1. [Overview](#overview)  
2. [Prerequisites](#prerequisites)  
3. [Installation](#installation)  
4. [Environment Variables](#environment-variables)  
5. [Usage](#usage)  
6. [Run the App](#run-the-app)  
7. [Testing & Logs](#testing--logs)  
8. [Troubleshooting](#troubleshooting)

---

## Overview

This Flask application uses:
- **xumm-sdk** for creating payloads that allow users to sign transactions (like SignIn, TrustSet, and OfferCreate) in the XUMM wallet.
- **xrpl-py** for interacting with the XRP Ledger (fetching balance, trustlines, etc.).
- **Flask** to provide the web interface and REST APIs.

Users initiate the sign-in process via a XUMM payload, which once signed, gives the application the user’s wallet address to facilitate further actions on the XRP Ledger.

---

## Prerequisites

1. **Python 3.7+**  
   Make sure you have Python 3.7 or newer installed:
   ```
   python --version
or



python3 --version
pip (Python package manager)
Typically installed by default with Python. Verify with:



pip --version
or



pip3 --version
(Recommended) Virtual Environment
Using a virtual environment (e.g., venv) is a best practice to isolate dependencies.

Installation
Clone or download this repository.
Navigate into the project folder:


cd your_project_directory
Create and activate a virtual environment (optional but recommended):


python -m venv venv
source venv/bin/activate  # On macOS/Linux
# or
venv\Scripts\activate     # On Windows
Install the required packages:


pip install -r requirements.txt
or if no requirements.txt is provided, manually install:


pip install flask xumm xrpl-py
Environment Variables
You must set environment variables for your XUMM API credentials:

XUMM_API_KEY
XUMM_API_SECRET
macOS/Linux Example


export XUMM_API_KEY="YOUR_XUMM_API_KEY"
export XUMM_API_SECRET="YOUR_XUMM_API_SECRET"
Windows (Command Prompt) Example
cmd

set XUMM_API_KEY=YOUR_XUMM_API_KEY
set XUMM_API_SECRET=YOUR_XUMM_API_SECRET
Windows (PowerShell) Example
powershell

$env:XUMM_API_KEY="YOUR_XUMM_API_KEY"
$env:XUMM_API_SECRET="YOUR_XUMM_API_SECRET"
Note: You can also integrate with a .env file and a library like python-dotenv, but that is beyond the scope of this README.

Usage
Export or set your environment variables as described above.
Run the Flask application (see the next section).
Open your browser at http://127.0.0.1:5000 and use the web interface to:
Connect your wallet via XUMM.
Check your XRP balance and trustlines.
Add trustlines.
Create trades (OfferCreate transactions).
Run the App
Development Mode
From within your project directory and with your environment variables set:



flask run
The default port is 5000. Navigate to http://127.0.0.1:5000 to access the app.

Production Mode
You may want to run this Flask app behind a production-grade WSGI server like Gunicorn or uWSGI, e.g.:



pip install gunicorn
gunicorn --bind 0.0.0.0:5000 app:app
Then configure a reverse proxy like Nginx to route traffic to Gunicorn.

Testing & Logs
Logging is set to DEBUG by default. You can change the level in the source code.
View logs in the console where you run the Flask app.
Test endpoints using tools like Postman or curl if needed.




Troubleshooting

XUMM API credentials not found
Ensure XUMM_API_KEY and XUMM_API_SECRET are set in your environment.
Cannot connect to XRPL
Check if https://s1.ripple.com:51234/ is reachable.
Missing dependencies
Install them via pip install -r requirements.txt.
CORS issues
If accessing the API from a different domain, you may need to enable or configure CORS.
