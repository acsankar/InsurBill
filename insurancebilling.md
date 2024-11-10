
# **InfyBILL System Documentation**

## **Table of Contents**

1. [Introduction](#introduction)
    - Purpose
    - Scope
    - Audience
2. [System Overview](#system-overview)
    - Application Description
    - Key Features
    - System Architecture
3. [System Requirements](#system-requirements)
    - Hardware Requirements
    - Software Requirements
    - Network Requirements
4. [Installation and Deployment](#installation-and-deployment)
    - Pre-Installation Checklist
    - Installation Steps
    - Post-Installation Configuration
5. [Configuration Details](#configuration-details)
    - Environment Variables
    - Configuration Files
    - Database Configuration
    - Network Configuration
    - Security Settings
6. [Getting Started](#getting-started)
    - Accessing InfyBILL
    - Login Procedure
    - User Roles and Permissions
7. [Main Menu Navigation](#main-menu-navigation)
    - Overview
    - Navigation Instructions
8. [Module Details](#module-details)
    - Client Management
    - Policy Management
    - Billing Operations
    - Payment Processing
    - Reports and Analytics
    - Administration
9. [Screen-by-Screen Guide](#screen-by-screen-guide)
    - Screen Layout
    - Field Descriptions
    - Navigation Steps
    - Common Actions
10. [System Maintenance](#system-maintenance)
    - Backup Procedures
    - Recovery Procedures
    - Performance Tuning
    - Log Management
11. [Error Messages and Troubleshooting](#error-messages-and-troubleshooting)
    - Common Error Codes
    - Resolution Steps
12. [Best Practices](#best-practices)
    - Data Entry Guidelines
    - Security Recommendations
13. [Frequently Asked Questions](#frequently-asked-questions)
14. [Appendices](#appendices)
    - Glossary of Terms
    - Keyboard Shortcuts
    - Contact Support

---

## **1. Introduction**

### **Purpose**

This document provides a comprehensive technical guide to **InfyBILL**, detailing its functionalities, technical specifications, installation procedures, configuration settings, and user interface components. It aims to assist system administrators, IT professionals, and end-users in effectively installing, configuring, and utilizing the application for billing insurance clients.

### **Scope**

The documentation covers:

- Technical architecture and system design
- Installation and deployment instructions
- Detailed configuration settings
- User interfaces and navigation steps
- Maintenance and troubleshooting procedures

### **Audience**

This guide is intended for:

- System Administrators
- IT Support Personnel
- Billing Specialists
- Insurance Agents
- New Users requiring training on InfyBILL

---

## **2. System Overview**

### **Application Description**

**InfyBILL** is a robust mainframe application designed to streamline the billing process for insurance clients. It handles client information, policy details, billing cycles, payments, and reporting. The application operates in an IBM z/OS mainframe environment, utilizing CICS (Customer Information Control System) for transaction processing and DB2 for data management.

### **Key Features**

- **Client Management**: Maintain and update client profiles.
- **Policy Management**: Access and modify policy details.
- **Billing Operations**: Generate invoices and manage billing cycles.
- **Payment Processing**: Record and process client payments.
- **Reports and Analytics**: Generate financial and operational reports.
- **Administration**: User management and system configuration.

### **System Architecture**

- **Presentation Layer**: 3270 terminal interface accessed via terminal emulators.
- **Application Layer**: CICS transaction programs written in COBOL.
- **Data Layer**: IBM DB2 relational database for data storage.
- **Security**: RACF (Resource Access Control Facility) for access control.
- **Batch Processing**: JCL (Job Control Language) scripts for batch jobs.

---

## **3. System Requirements**

### **Hardware Requirements**

- **Mainframe Server**: IBM zSeries or equivalent
    - **CPU**: Sufficient processing power to handle transaction loads
    - **Memory**: Minimum 8 GB RAM allocated to InfyBILL applications
    - **Storage**: Minimum 500 GB of disk space for application and data
- **Client Workstations**:
    - **CPU**: Dual-core processor
    - **Memory**: 4 GB RAM
    - **Storage**: 100 MB for terminal emulator software
    - **Display**: VGA or higher resolution monitor

### **Software Requirements**

- **Mainframe Environment**:
    - **Operating System**: IBM z/OS version 2.3 or higher
    - **CICS**: Version 5.5 or higher
    - **DB2**: Version 12 for z/OS
    - **RACF**: For security and access control
- **Client Workstations**:
    - **Operating System**: Windows 10 or higher, macOS Catalina or higher
    - **Terminal Emulator**: IBM Personal Communications, Micro Focus Rumba, or equivalent
    - **Java Runtime Environment**: JRE 8 or higher (if required by emulator)

### **Network Requirements**

- **Connectivity**: Stable TCP/IP connection between client workstations and mainframe server
- **Bandwidth**: Minimum 1 Mbps per client session
- **Ports**: Ensure that port 23 (Telnet) or configured TN3270 port is open
- **VPN Access**: For remote connections, a secure VPN is required

---

## **4. Installation and Deployment**

### **Pre-Installation Checklist**

- **Hardware Setup**: Ensure the mainframe hardware meets the specified requirements.
- **Software Licenses**: Obtain necessary licenses for CICS, DB2, and terminal emulators.
- **User Accounts**: Set up system administrator accounts with appropriate permissions.
- **Network Configuration**: Verify network connectivity between clients and the mainframe.

### **Installation Steps**

#### **Mainframe Server Installation**

1. **Operating System Preparation**:
    - Install or verify the IBM z/OS operating system.
    - Apply the latest service packs and patches.

2. **Database Setup**:
    - Install IBM DB2 for z/OS.
    - Create the InfyBILL database instance.
    - Execute the DDL scripts provided to create necessary tables and indexes.

3. **CICS Configuration**:
    - Install CICS Transaction Server.
    - Define the CICS region for InfyBILL.
    - Configure transaction definitions, programs, and file control tables.

4. **Application Deployment**:
    - Compile the COBOL programs using the provided source code.
    - Load the compiled programs into the CICS region.
    - Deploy resource definitions for screens, maps, and transactions.

5. **Security Setup**:
    - Configure RACF profiles and permissions.
    - Define user groups and assign appropriate access levels.

#### **Client Workstation Installation**

1. **Terminal Emulator Installation**:
    - Install the chosen terminal emulator software.
    - Configure session settings to connect to the mainframe host.

2. **Java Installation** (if required):
    - Install the latest JRE compatible with the terminal emulator.

3. **Network Configuration**:
    - Ensure the workstation can reach the mainframe IP address.
    - Configure VPN if accessing remotely.

### **Post-Installation Configuration**

- **Environment Variables**:
    - Set necessary environment variables for application paths and configurations.
- **Testing**:
    - Perform connectivity tests from client workstations.
    - Execute test transactions to verify system functionality.
- **Backup Configuration**:
    - Set up automated backups for the database and application files.

---

## **5. Configuration Details**

### **Environment Variables**

- **CICS_APPLID**: Application identifier for the CICS region.
- **DB2_DBNAME**: Name of the DB2 database instance.
- **INFYBILL_HOME**: Root directory of the InfyBILL application on the mainframe.

### **Configuration Files**

- **DFHCSD**: CICS System Definition file containing resource definitions.
- **DB2 Connection Config**: Contains database connection parameters.

### **Database Configuration**

- **Database Name**: INFYBILL_DB
- **Tablespaces**:
    - **CLIENT_TS**: Stores client-related tables.
    - **POLICY_TS**: Stores policy information.
    - **BILLING_TS**: Stores billing and transaction data.
- **User Accounts**:
    - **DB2INFYADM**: Database administrator account.
    - **DB2INFYUSR**: Application user account with limited permissions.

### **Network Configuration**

- **Mainframe Hostname/IP**: 192.168.100.10 (example)
- **TN3270 Port**: 23 or custom port as configured.
- **VPN Settings**:
    - **VPN Type**: IPSec
    - **VPN Endpoint**: vpn.infybill.com
    - **Authentication**: Two-factor authentication required.

### **Security Settings**

- **RACF Configuration**:
    - **Groups**:
        - **INFYADM**: System administrators.
        - **INFYUSR**: Standard users.
    - **Permissions**:
        - Assign access to datasets, transactions, and resources based on group.
- **Password Policies**:
    - **Minimum Length**: 8 characters.
    - **Complexity**: Must include letters, numbers, and special characters.
    - **Expiration**: Passwords expire every 90 days.

---

## **6. Getting Started**

### **Accessing InfyBILL**

1. **Launch Terminal Emulator**:
    - Open IBM Personal Communications or your chosen emulator.
2. **Create a New Session**:
    - **Connection Type**: TN3270.
    - **Host Name/IP Address**: Enter the mainframe's IP or hostname.
    - **Port**: Enter the configured TN3270 port.
3. **Configure Session Settings**:
    - **Terminal Type**: IBM-3278 Model 2.
    - **Screen Size**: 24 rows x 80 columns.
4. **Connect to the Mainframe**:
    - Save the session profile for future use.
    - Click **Connect**.

### **Login Procedure**

1. **Mainframe Login Screen**:
    - **User ID Field**: Enter your mainframe User ID.
    - **Password Field**: Enter your password.
    - Press **Enter**.
2. **Access CICS Region**:
    - At the command prompt, enter **CICSTS** (or the configured CICS transaction ID).
    - Press **Enter** to access the CICS region.
3. **InfyBILL Application Entry**:
    - On the CICS welcome screen, enter **INFYBILL**.
    - Press **Enter** to launch the application.

### **User Roles and Permissions**

- **Standard User**:
    - **Access**: Client Management, Policy Management, Payment Processing.
- **Supervisor**:
    - **Access**: All Standard User modules plus Billing Operations.
- **Administrator**:
    - **Access**: Full access including Administration and system configuration.

---

## **7. Main Menu Navigation**

### **Overview**

Upon launching InfyBILL, the **Main Menu** displays all available modules. Navigation is primarily keyboard-based, utilizing function keys and command inputs.

### **Navigation Instructions**

- **Selecting Options**:
    - Type the **Menu Option Number** next to the desired module.
    - Press **Enter** to proceed.
- **Function Keys**:
    - **F1**: Help.
    - **F3**: Exit or return to the previous menu.
    - **F12**: Logout of the application.
- **Command Line**:
    - Some screens allow direct commands. Enter the command at the prompt and press **Enter**.

**Main Menu Options**:

1. Client Management
2. Policy Management
3. Billing Operations
4. Payment Processing
5. Reports and Analytics
6. Administration
7. Logout

---

## **8. Module Details**

### **Client Management**

#### **Accessing Client Management**

- From the **Main Menu**, enter **1** and press **Enter**.

#### **Features**

- **Search Clients**:
    - **Command**: Enter **SC** at the prompt.
    - **Parameters**: Client ID, Name, or other identifiers.
- **Add New Client**:
    - **Command**: Enter **AC**.
    - **Fields**: Name, Address, Contact Information, Date of Birth, etc.
- **Update Client Details**:
    - **Command**: Enter **UC** followed by the Client ID.

### **Policy Management**

#### **Accessing Policy Management**

- From the **Main Menu**, enter **2** and press **Enter**.

#### **Features**

- **Search Policies**:
    - **Command**: Enter **SP**.
    - **Parameters**: Policy Number, Client ID.
- **Create Policy**:
    - **Command**: Enter **CP**.
    - **Fields**: Policy Type, Coverage Details, Effective Date, Premium Amount.
- **Modify Policy**:
    - **Command**: Enter **MP** followed by the Policy Number.

*(Additional module details continue similarly for Billing Operations, Payment Processing, Reports and Analytics, and Administration.)*

---

## **9. Screen-by-Screen Guide**

### **Screen Layout**

- **Header**:
    - Displays application name, module, user ID, and session timestamp.
- **Body**:
    - Contains input fields, data tables, or forms.
- **Footer**:
    - Shows function key mappings, status messages, and prompts.

### **Field Descriptions**

- **Field Types**:
    - **Alphanumeric Fields**: Accept letters and numbers.
    - **Numeric Fields**: Accept numbers only.
    - **Date Fields**: Format as YYYY-MM-DD.
- **Field Indicators**:
    - **Asterisk (*)**: Mandatory field.
    - **Underline (_)**: Editable field.
    - **Protected Field**: Non-editable, display-only information.

### **Navigation Steps**

#### **Example: Processing a Payment**

1. **Access Payment Processing**:
    - From the Main Menu, enter **4** and press **Enter**.
2. **Select Record Payment**:
    - Enter **RP** at the command prompt.
3. **Payment Entry Screen** appears.
    - **Client ID***: Enter the client's ID.
    - **Policy Number***: Enter the policy number.
    - **Payment Amount***: Enter the amount received.
    - **Payment Date***: Defaults to the current date; modify if necessary.
    - **Payment Method***: Select from options (e.g., Cash, Check, Credit Card).
4. **Submit Payment**:
    - Press **F10** to submit.
5. **Confirmation Screen**:
    - Displays a summary of the transaction.
    - Press **F3** to return to the Payment Processing menu.

### **Common Actions**

- **F2**: Search.
- **F4**: Edit.
- **F5**: Refresh/Reload.
- **F7/F8**: Scroll up/down in lists.
- **F9**: Print.
- **F10**: Save/Submit.
- **F11**: Details/View More.

---

## **10. System Maintenance**

### **Backup Procedures**

- **Database Backups**:
    - Schedule nightly backups using IBM's DB2 utilities.
    - Use incremental backups during off-peak hours.
- **Application Backups**:
    - Backup application libraries and configuration files weekly.
- **Storage Location**:
    - Secure backups on separate storage devices or off-site locations.

### **Recovery Procedures**

- **Disaster Recovery Plan**:
    - Maintain a hot standby mainframe with real-time data replication.
- **Restoration Steps**:
    1. Identify the point of failure.
    2. Restore the database from the latest backup.
    3. Recover transaction logs to bring the database to the current state.
    4. Restart CICS regions and verify system integrity.

### **Performance Tuning**

- **Database Optimization**:
    - Regularly update database statistics.
    - Reorganize tablespaces to prevent fragmentation.
- **CICS Tuning**:
    - Monitor transaction response times.
    - Adjust MAXTASKS and TCLASS parameters for optimal throughput.
- **Monitoring Tools**:
    - Utilize IBM OMEGAMON or similar tools for real-time performance monitoring.

### **Log Management**

- **System Logs**:
    - Rotate logs daily to prevent storage issues.
    - Archive logs for at least one year for auditing purposes.
- **Error Logs**:
    - Set up alerts for critical errors.
    - Review logs weekly to identify and address recurring issues.

---

## **11. Error Messages and Troubleshooting**

### **Common Error Codes**

- **CICS001**: "Transaction Aborted Due to Timeout."
    - **Resolution**: Check system performance; increase transaction timeout settings if necessary.
- **DB2001**: "Database Connection Failure."
    - **Resolution**: Verify DB2 instance is running; check network connectivity.
- **SEC1001**: "Unauthorized Access Attempt Detected."
    - **Resolution**: Ensure the user has the necessary permissions; review RACF settings.

### **Resolution Steps**

- **Step 1**: Consult the error code reference in the appendices.
- **Step 2**: Use system logs to gather more information.
- **Step 3**: If unable to resolve, escalate to the system administrator or vendor support.

---

## **12. Best Practices**

### **Data Entry Guidelines**

- **Consistency**: Use standardized formats for data entry to ensure data integrity.
- **Validation**: Double-check entries before submitting transactions.
- **Confidentiality**: Follow company policies for handling sensitive client information.

### **Security Recommendations**

- **Access Control**: Regularly review user access levels and revoke permissions when necessary.
- **Audit Trails**: Enable auditing features to track user activities.
- **Incident Response**: Have a plan in place for responding to security breaches.

---

## **13. Frequently Asked Questions**

1. **How do I add a new user to InfyBILL?**
   - Access the **Administration** module (Option **6**), select **User Management**, and follow the prompts to add a new user. Assign appropriate roles and permissions.

2. **What should I do if I encounter a database error?**
   - Record the error code and message, check the DB2 instance status, and consult the **Error Messages and Troubleshooting** section.

3. **How can I improve system performance during peak hours?**
   - Review the **Performance Tuning** guidelines. Consider adjusting CICS parameters and optimizing database queries.

---

## **14. Appendices**

### **Glossary of Terms**

- **CICS**: Customer Information Control System, a transaction server that runs primarily on IBM mainframe systems.
- **DB2**: IBM's database management system.
- **RACF**: Resource Access Control Facility, IBM's mainframe security system.
- **JCL**: Job Control Language used on IBM mainframes to instruct the system on how to run batch jobs.

### **Keyboard Shortcuts**

*(Include a comprehensive list of keyboard shortcuts and their functions.)*

### **Contact Support**

- **Technical Support Email**: support@infybill.com
- **Help Desk Phone**: +1 (800) 555-1234
- **Emergency Support**: Available 24/7 for critical issues
- **Support Portal**: [support.infybill.com](http://support.infybill.com)
- **Support Hours**: Monday to Friday, 9 AM to 5 PM EST (non-emergency)

---

**Note**: This documentation is intended to serve as a comprehensive technical guide. Users and administrators should ensure they are familiar with company policies, compliance regulations, and standard operating procedures related to billing and data management.

---

**End of Document**
