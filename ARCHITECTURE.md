# Roofers App – Architecture Overview

## Overview
Roofers App is a closed‑source Windows `.exe` application built for offline operation, secure license enforcement, and automated reporting. It provides a fast, local Operational CRM tailored specifically for **roofing production workflows**, including tear‑off, installation, repairs, payroll, and material tracking.

Unlike cloud‑based CRMs, the system runs entirely on the user’s machine or internal network, ensuring reliability, data ownership, and zero external dependencies.

The application supports both **SQL Server Express** and **Full SQL Server**, selected during installation.

---

# Architecture

## Database Selection (Installer‑Driven)
During installation, the user selects one of two supported database modes:

### 1. SQL Server Express (Local Database – Recommended for 1–5 Users)
- Installer automatically installs and configures SQL Server Express  
- Ideal for single‑machine setups or small office networks  
- No licensing cost  

### 2. Full SQL Server (Standard/Enterprise)
- User connects to an existing SQL Server instance  
- Supports multi‑user environments and IT‑managed deployments  
- Designed for medium to large roofing companies  

The installer writes a registry flag (`UseSQLExpress`) that determines which connection setup page the application loads on first launch.

---

## License Enforcement Flow
**User Launch → License Prompt → Gumroad API Validation → Local Unlock**

- User enters their Gumroad license key on first launch  
- Key is validated through Gumroad’s `/v2/licenses/verify` endpoint  
- Valid keys unlock the application and store the license state locally  
- Periodic revalidation may occur (e.g., every 7 days)  
- License tier determines access to Basic, Pro, or Enterprise features  

---

## Local Session Context
- All data is stored in SQL Server Express or Full SQL Server  
- No cloud sync, Redis, or external session store  
- Secure login using salted + hashed admin credentials  
- Fully offline operation after initial license activation  

---

## Data Transfer Between Computers
The app includes a built‑in SQL migration tool for moving data to a new machine:

- Creates a `.bak` backup file from the old computer  
- Restores the `.bak` file on the new computer  
- Works for both SQL Express and Full SQL Server  
- Ideal for machine upgrades or office migrations  

---

## SQL Connection Pages
The application routes users to the correct connection setup page based on installer selection:

- `sql_connection_page.py` – SQL Express  
- `sql_server_connection_page.py` – Full SQL Server  

Both pages support:
- Connection testing  
- Credential validation  
- Database creation (if needed)  
- Secure admin login setup  

---

## Payroll & Work Ticket Workflow
**Admin Login → Roofing Work Ticket Entry → Payroll Calculation → Excel Export**

- Admin enters job details, roofing crew info, materials used, and tasks completed  
- Payroll supports multiple calculation methods:
  - **Squares installed × rate**  
  - **Bundles / rolls / LF × rate**  
  - **Hourly wage**  
  - **Flat rate per job**  
- Pay is automatically split across workers per job  
- Excel payroll reports are generated two days after the pay period ends  

---

## File Storage & Export
All reports are stored locally
