# E-Invoicing API Platform for SMEs - User Stories and Analysis

## Project Overview

This project aims to develop a web application that streamlines e-invoicing processes for Small and Medium Enterprises (SMEs) by leveraging e-invoicing APIs. The application will provide a user-friendly GUI that demonstrates various e-invoicing API endpoints and their functions, focusing on three main categories:

1. **Invoice Creation** - Converting data from various formats into standardized UBL XML invoices
2. **Invoice Validation** - Validating invoices against Australian e-invoicing standards
3. **Invoice Sending/Receiving** - Transmitting invoices to recipients through different protocols

The application will serve as a SaaS (Software as a Service) solution, allowing SMEs to create, validate, and send e-invoices without the need for expensive, inflexible vendor solutions.

## Core Purpose

The core purpose of this application is to:

- Provide SMEs with a cost-effective, flexible e-invoicing solution
- Reduce manual intervention and errors in the invoicing process
- Demonstrate the functionality of e-invoicing APIs through an intuitive GUI
- Support Australian e-invoicing standards (UBL 2.1 XML format)
- Enable SMEs to comply with e-invoicing regulations without vendor lock-in

## User Personas

1. **Small Business Owner** - Has limited technical knowledge but needs to comply with e-invoicing regulations
2. **Accountant/Bookkeeper** - Manages invoices for SMEs and needs an efficient way to create and send compliant e-invoices
3. **IT Administrator** - Responsible for implementing e-invoicing solutions in an SME

## User Stories

### Authentication & User Management

1. **User Registration**

   - As a new user, I want to register for an account so that I can access the e-invoicing platform.
   - Acceptance Criteria:
     - User can enter email, password, and business details
     - System validates input and creates a new account
     - User receives confirmation email

2. **User Login**

   - As a registered user, I want to log in to the platform so that I can access my e-invoicing tools.
   - Acceptance Criteria:
     - User can enter email and password
     - System authenticates credentials
     - User is directed to the dashboard upon successful login

3. **Password Reset**
   - As a user who forgot my password, I want to reset it so that I can regain access to my account.
   - Acceptance Criteria:
     - User can request password reset via email
     - System sends reset link
     - User can create a new password

### Invoice Creation

4. **CSV/Excel to E-Invoice Conversion**

   - As a business owner, I want to upload my CSV/Excel invoice data so that it can be converted to a standardized e-invoice.
   - Acceptance Criteria:
     - User can upload CSV/Excel files
     - System extracts invoice data
     - System generates UBL XML invoice
     - User can download or proceed with the generated invoice

5. **Manual Invoice Creation Form**

   - As an accountant, I want to manually enter invoice details through a form so that I can create an e-invoice without existing digital data.
   - Acceptance Criteria:
     - User can fill out a form with all required invoice fields
     - System validates input in real-time
     - System generates UBL XML invoice
     - User can download or proceed with the generated invoice

6. **PDF Invoice Data Extraction**
   - As a business owner, I want to upload PDF invoices so that the system can extract data and convert it to a standardized e-invoice.
   - Acceptance Criteria:
     - User can upload PDF invoices
     - System extracts data using OCR
     - User can review and correct extracted data
     - System generates UBL XML invoice

### Invoice Validation

7. **Validate E-Invoice**

   - As a user, I want to validate my e-invoice against Australian standards so that I can ensure compliance before sending.
   - Acceptance Criteria:
     - User can upload or select a UBL XML invoice
     - System validates against wellformedness, syntax rules, PEPPOL rules, and schema
     - System displays validation results with clear error messages
     - User can download validation report

8. **View Validation Report**
   - As a user, I want to view a detailed validation report so that I can understand and fix any issues with my e-invoice.
   - Acceptance Criteria:
     - System displays validation errors with explanations
     - User can see which specific rules were violated
     - System provides suggestions for fixing errors where possible
     - User can download the report in different formats (JSON, HTML, PDF)

### Invoice Sending

9. **Send E-Invoice via Email**

   - As a user, I want to send my e-invoice via email so that my client can receive it electronically.
   - Acceptance Criteria:
     - User can select a validated e-invoice
     - User can enter recipient email address
     - System sends the e-invoice as an attachment
     - User receives confirmation and delivery status

10. **Send E-Invoice via SFTP**
    - As a user, I want to send my e-invoice via SFTP so that it can be securely transferred to systems that support this protocol.
    - Acceptance Criteria:
      - User can select a validated e-invoice
      - User can enter SFTP connection details
      - System transfers the e-invoice
      - User receives confirmation and transfer status

### Dashboard & Management

11. **View Invoice History**

    - As a user, I want to view my invoice history so that I can track and manage all my e-invoices.
    - Acceptance Criteria:
      - User can see a list of all created/validated/sent invoices
      - User can filter and search invoices
      - User can view invoice details
      - User can download invoices in UBL XML format

12. **View API Documentation**
    - As a user, I want to view documentation about the e-invoicing APIs so that I can understand how they work.
    - Acceptance Criteria:
      - User can access documentation for each API endpoint
      - Documentation includes request/response formats
      - Documentation includes authentication methods
      - Documentation includes error handling procedures

## Development Analysis

### Core Features (Must-Have)

1. User authentication (registration, login, password reset)
2. Invoice creation from CSV/Excel
3. Manual invoice creation form
4. Invoice validation against Australian standards
5. Email sending functionality
6. Dashboard to view invoice history
7. Basic API documentation

### Secondary Features (Nice-to-Have)

1. PDF invoice data extraction
2. SFTP sending functionality
3. Advanced validation report with fix suggestions
4. Multiple report formats (JSON, HTML, PDF)

### Development Considerations

1. **Technology Stack**

   - Frontend: React.js with ShadcnUI and tailwindCss
   - Backend: DotNet Web API
   - Database: MS-SQL
   - Authentication: Clerk

2. **API Integration**

   - Focus on integrating with one reliable API for each category initially
   - Consider ESS Validator for validation as mentioned in the specs
   - Explore Storecove API for sending if PEPPOL network is selected

3. **Development Timeline (6 weeks)**

   - Week 1: Project setup, authentication, and basic UI
   - Week 2-3: Invoice creation features
   - Week 3-4: Invoice validation features
   - Week 4-5: Invoice sending features
   - Week 5-6: Dashboard, testing, and bug fixes

4. **Scope Limitations**
   - Focus on the core e-invoicing workflow rather than advanced features
   - Limit the number of input formats supported initially
   - Start with email as the primary sending method before adding SFTP
   - Focus on Australian UBL standards only

## Page Structure Analysis

Based on the user stories and requirements, the following pages will be needed to create a comprehensive and user-friendly e-invoicing platform:

### 1. Authentication Pages

- **Landing Page** - Introduction to the platform with login/register options
- **Registration Page** - Form for new users to create an account
- **Login Page** - Form for existing users to log in
- **Password Reset Page** - Form to request and process password resets

### 2. Dashboard Pages

- **Main Dashboard** - Overview of recent activity, quick access to main functions
  - Summary statistics (invoices created, validated, sent)
  - Recent invoices
  - Quick action buttons for main functions

### 3. Invoice Creation Pages

- **Creation Method Selection Page** - Options to choose how to create an invoice
- **CSV/Excel Upload Page** - Interface for uploading and mapping CSV/Excel files
  - File upload area
  - Column mapping interface
  - Preview of extracted data
- **Manual Invoice Form Page** - Form with all required fields for manual invoice creation
  - Structured form with sections for:
    - Seller details
    - Buyer details
    - Invoice details (date, number, etc.)
    - Line items
    - Tax information
    - Payment terms
  - Real-time validation
- **PDF Upload Page** (secondary feature) - Interface for uploading PDF invoices
  - File upload area
  - Data extraction preview
  - Correction interface

### 4. Invoice Validation Pages

- **Validation Page** - Interface to upload or select invoices for validation
  - File upload area or selection from existing invoices
  - Validation options
  - Submit button
- **Validation Results Page** - Detailed display of validation results
  - Summary of validation status
  - Detailed error list with explanations
  - Suggestions for fixes
  - Options to download report in different formats

### 5. Invoice Sending Pages

- **Sending Method Selection Page** - Options to choose how to send an invoice
- **Email Sending Page** - Form to send invoice via email
  - Invoice selection
  - Recipient details
  - Email content customization
  - Send button
- **SFTP Sending Page** (secondary feature) - Form to send invoice via SFTP
  - Invoice selection
  - SFTP connection details
  - Send button

### 6. Management Pages

- **Invoice History Page** - List of all invoices with filtering and search
  - Sortable and filterable table of invoices
  - Search functionality
  - Action buttons (view, download, send)
- **Invoice Detail Page** - Detailed view of a specific invoice
  - Complete invoice information
  - Status information
  - Action buttons (validate, send, download)
- **API Documentation Page** - Documentation for the e-invoicing APIs
  - Endpoint descriptions
  - Request/response formats
  - Authentication methods
  - Error handling procedures

### 7. Settings Pages

- **Account Settings Page** - User profile and account settings
  - Personal information
  - Business details
  - Password change
- **Preferences Page** - User preferences for the platform
  - Default settings for invoice creation
  - Email templates
  - Notification preferences

### Page Flow Diagram

The user journey through these pages would typically follow this flow:

1. User registers/logs in → Dashboard
2. From Dashboard:
   - Create Invoice → Creation Method Selection → Specific Creation Page → Preview → Save/Validate
   - Validate Invoice → Validation Page → Validation Results
   - Send Invoice → Sending Method Selection → Specific Sending Page → Confirmation
   - View History → Invoice History → Invoice Detail
   - View Documentation → API Documentation

## UI/UX Considerations

1. **Consistent Layout**

   - Maintain a consistent header, navigation, and footer across all pages
   - Use a sidebar for main navigation categories
   - Implement breadcrumbs for easy navigation between related pages

2. **Responsive Design**

   - Ensure all pages work well on desktop, tablet, and mobile devices
   - Prioritize important actions on smaller screens

3. **User Guidance**

   - Implement tooltips and help text for complex fields
   - Provide clear error messages and validation feedback
   - Include progress indicators for multi-step processes

4. **Accessibility**

   - Ensure proper contrast ratios for text
   - Include alt text for images
   - Support keyboard navigation
   - Make forms screen-reader friendly

5. **Performance**
   - Implement lazy loading for large data tables
   - Optimize file uploads and processing
   - Show loading indicators for API calls

## Conclusion

This project will deliver a functional e-invoicing platform that demonstrates the capabilities of e-invoicing APIs through a user-friendly GUI. By focusing on the core features of invoice creation, validation, and sending, the application will provide SMEs with a cost-effective solution for complying with e-invoicing regulations.

The development plan is designed to be achievable by two interns within a 6-week timeframe by prioritizing essential features and limiting scope to the most critical functionality. The user stories outlined above capture the core requirements while ensuring the project remains manageable within the given constraints.

The page structure outlined above provides a comprehensive framework for implementing all the required functionality while maintaining a clean, intuitive user experience. By focusing on the core pages first and adding secondary features later, the development team can ensure timely delivery of a functional product.
