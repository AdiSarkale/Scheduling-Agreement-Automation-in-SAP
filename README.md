# Scheduling Agreement Automation in SAP (ME38)

> **Copyright & Usage Notice**  
> Copyright © 2026 Aditya Sarkale. All rights reserved **to the extent of rights owned by the author**.  
> No license is granted to copy, modify, redistribute, publish, sublicense, or use this source code or substantial portions of it outside the GitHub platform without prior written permission from the applicable rights holder.  
> **Important:** Any company-owned, client-owned, SAP-proprietary, third-party, or otherwise restricted material remains subject to its applicable ownership, confidentiality, and licensing terms.

## Overview
A React + Flask application that automates SAP Scheduling Agreement processing through transaction **ME38** using **SAP GUI Scripting** on Windows.

The application is designed for structured, repeatable processing of scheduling-agreement schedule-line updates from CSV input.

## Business Workflow
1. Prepare the required CSV input.
2. Start SAP GUI for Windows and log in.
3. Start the Flask backend.
4. Start the React frontend.
5. Upload the CSV and submit the process.
6. Python connects to the active SAP GUI scripting session.
7. The automation opens ME38, navigates to the relevant agreement/item and processes schedule lines.
8. SAP status messages are returned to the application.
9. Validate the result in SAP.

## Technology Stack
- Python / Flask
- pywin32 / SAP GUI Scripting
- React
- JavaScript / HTML / CSS
- CSV processing

## Prerequisites
- Windows
- SAP GUI for Windows
- SAP GUI Scripting enabled on the client
- SAP server-side scripting enabled by the authorized SAP Basis team
- Python 3.x
- Node.js / npm
- Appropriate SAP authorization

### SAP GUI Scripting
The automation requires access to the SAP GUI scripting API. If the automation reports that SAP is not logged in or the transaction was cancelled, check the documented RZ11 configuration with the SAP Basis team.

## Repository Structure
```
backend/       Flask API and SAP GUI automation
frontend/      React UI
ME38.csv       Example/template input
```

## Setup

### Backend
```powershell
cd backend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

If the repository does not contain a `requirements.txt` in the backend directory, install the Python dependencies documented by the current project files before starting the backend.

### Frontend
```powershell
cd frontend
npm install
npm start
```

Use the command defined in the project's `package.json` if it differs.

## Input
Use the supplied CSV template and preserve the required columns and formats used by the automation. Do not commit production or confidential business data.

## Troubleshooting
### SAP appears logged in but automation says "SAP not logged in or User cancelled the transaction"
- Confirm SAP GUI is running and the correct user session is logged in.
- Check the RZ11 configuration required for GUI scripting.
- Confirm the relevant dynamic scripting parameter is `TRUE`.
- Check whether the SAP session was cancelled or is unavailable to the script.
- Escalate server-side configuration changes to SAP Basis.

### Automation controls the wrong SAP session
Close unused SAP GUI sessions or ensure the application is pointed at the intended active scripting session.

## Security
Never hard-code SAP credentials. Do not commit passwords, tokens, cookies, confidential company data, production exports, or restricted SAP information.

## Maintenance
Keep business-rule changes documented. Test the automation against a controlled/non-production SAP environment before production use.

## Author
**Aditya Sarkale** — GitHub: https://github.com/AdiSarkale
