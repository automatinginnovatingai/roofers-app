Roofers App – README.txt
====================================
Version: 2.0.0

Welcome to the Automating Innovating AI Roofers App — a streamlined, secure, and intuitive tool
for managing roofing production workflows, employee payroll, material usage, inventory, and data exports.


====================================
Role‑Based Access Control (RBAC)
====================================
All AIAI applications now include a unified, secure RBAC system designed for multi‑admin environments
and professional data governance.

Global Admin
------------
• Created during first registration  
• Full system access  
• Generates company_id  
• Can add Local Admins  
• Can configure company‑wide settings  
• Can access all modules (payroll, materials, inventory, POs, reporting)

Local Admin
-----------
• Must be created by a Global Admin  
• No company creation privileges  
• No admin‑creation privileges  
• No session is created during registration — must log in after being added  
• Access limited to modules enabled by the Global Admin  
• All actions restricted to their assigned company_id

Admin‑Only Registration
-----------------------
• Only administrators can register accounts  
• No employee or installer self‑registration  

Dynamic UI Permissions
----------------------
• Screens automatically adapt to the user’s role  
• Restricted modules are hidden or blocked with clear access messages  

Centralized Permission Enforcement
----------------------------------
• All RBAC checks occur in Admin_Interface.py  
• Feature files do not perform their own permission checks  
• Ensures consistent, secure, and scalable access control  

Multi‑Admin Support
-------------------
• Global Admins may add additional administrators using the Admin Add‑on  
• Each admin receives their own secure login and role‑based access  


====================================
Key Features
====================================

Secure Login
------------
• Encrypted password protection with industry‑standard hashing  
• Salted + hashed credential verification  
• Required for all payroll, export, and admin operations  


Payroll Management
------------------
• Input and calculate daily and weekly roofing payroll  
• Supports multiple pay calculation methods:
  - Quantity × Pay Rate (e.g., 12 bundles × $8.50)
  - Per‑piece rates (e.g., 6 pipe boots × $12.00)
  - Hourly wage (e.g., 10 hours × $22.00)
  - Enter 0 in any field that does not apply
• Add up to four employees per job  
• Automatic pay splitting among listed employees  


Employee Job Entry
------------------
Each job entry requires:
• First and last name  
• Employee ID (optional)  
• Work hours and roofing job roles  
• Client name  
• Property address  
• Unit number  
• Roof area (Squares)  

Optional roofing material details:
• Shingles (Architectural, 3‑Tab)  
• Underlayment (Synthetic, Felt)  
• Ridge caps, starter strips, vents  
• Flashing, drip edge, pipe boots  
• Nails, rolls, bundles, linear‑footage items  


Pay Week Entry & Auto Export
----------------------------
This module streamlines payroll cycle management and Excel export automation.

• Set the start and end day of the payroll period  
  Example: Start = Thursday, End = Wednesday  
• Payroll auto‑exports 2 days after the end day  
• Fullscreen interface (press ESC to exit)  
• Requires verified admin session  

Export Details:
• Weekly payroll grouped by employee  
• Saved under:
  Documents/AIAI_Roofing_App/Payroll_Excels/YYYY-MM/Payroll_YYYY-MM.xlsx
• Each employee receives a dedicated sheet labeled by week number  
• Totals auto‑calculated  

After Export:
• You will be prompted to open the workbook immediately  
• Microsoft Excel must be installed  

Tip:
Ensure all pay data is complete before the scheduled export date (End Day + 2).  


Data Protection
---------------
• Automatic de‑duplication prevents redundant entries  
• All records tied to company_id for strict isolation  


Reporting
---------
• Clean Excel‑compatible CSV exports  
• Grouped by month/day  
• Customizable export file names  


Auto‑Updating
-------------
• Automatically checks for new app versions  
• Ensures you always run the latest stable release  


Friendly Interface
------------------
• Designed for field and office use  
• No technical knowledge required  


====================================
System Requirements
====================================
• Windows 10 or later  
• Microsoft Excel (required for viewing reports)  
• ~900 MB available disk space  
• SQL Server Express LocalDB for data storage  
• Monthly Excel files generated automatically  


====================================
License Activation
====================================
This app requires a valid Gumroad license key.

• You will be prompted to enter your license key on first launch  
• The app verifies your key securely via Gumroad’s API  
• Invalid or revoked licenses restrict access  

Note: Internet access is required for initial license validation.  


====================================
Getting Started
====================================
1. Launch the Roofers App  
2. Click “Admin Registration” to create the first Global Admin  
3. Log in using “Admin Login”  
4. Navigate to the Admin Interface  
5. Open “Employee Worksheet” to begin logging job and payroll data  


====================================
Navigation & Exiting
====================================
• Use the dashboard to access all modules  
• Click “Exit” on any screen to close the app  


====================================
Tips
====================================
• Export data regularly  
• Use strong admin credentials  
• Keep Excel updated  
• Ensure accurate job entry before payroll export  


====================================
Troubleshooting
====================================
App won’t launch:
• Ensure Windows 10+ is installed  
• Confirm Excel is available  

License key rejected:
• Verify your Gumroad purchase email  
• Ensure internet access for validation  

Export failed:
• Confirm pay data is complete  
• Ensure Excel is installed  

Auto‑update not working:
• Check internet connection  
• Review firewall settings  


====================================
Support
====================================
Questions or feedback?  
automatinginnovatingai@outlook.com

Thank you for using the Roofers App!
