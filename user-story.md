# E-Invoicing API Platform for SMEs - User Stories and Analysis

## Project Overview

This project aims to develop a web application that demonstrates e-invoicing API capabilities for Small and Medium Enterprises (SMEs) by leveraging the Reckon One API and supplementing it with additional services for Australian e-invoicing standards. The application will provide a user-friendly Website that demonstrates various e-invoicing API endpoints and their functions, focusing on three main categories:

1. **Invoice Creation** - Creating invoices via Reckon One API and converting to UBL XML format
2. **Invoice Validation** - Validating UBL XML invoices against Australian e-invoicing standards
3. **Invoice Sending** - Transmitting invoices via email and PEPPOL network

The application will serve as a SaaS solution, allowing SMEs to create, validate, and send e-invoices without the need for expensive, inflexible vendor solutions that comply with Australian standards

## Core Purpose

The core purpose of this application is to:

- Demonstrate the functionality of e-invoicing APIs through an intuitive GUI
- Show how Reckon One API can be integrated with UBL XML conversion for Australian standards
- Illustrate the validation process against Australian e-invoicing standards
- Demonstrate invoice sending via email and PEPPOL network
- Provide a reference implementation for SMEs considering e-invoicing solutions

## User Personas

1. **Small Business Owner** - Has limited technical knowledge but needs to comply with e-invoicing regulations
2. **Accountant/Bookkeeper** - Manages invoices for SMEs and needs an efficient way to create and send compliant e-invoices
3. **IT Administrator** - Responsible for implementing e-invoicing solutions in an SME

## User Stories

### Authentication & User Management

1. **User Registration** (CORE)

   - As a new user, I want to register for an account so that I can access the e-invoicing platform.
   - Acceptance Criteria:
     - User can enter email, password, and basic business details
     - System validates input and creates a new account
     - User receives confirmation email

2. **User Login** (CORE)

   - As a registered user, I want to log in to the platform so that I can access the e-invoicing tools.
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
     - System creates invoice in Reckon One via API
     - System converts Reckon invoice to UBL XML format
     - User can download or proceed with the generated UBL XML invoice

5. **Manual Invoice Creation Form** (CORE)

   - As an accountant, I want to manually enter invoice details through a form so that I can create an invoice without existing digital data.
   - Acceptance Criteria:
     - User can fill out a form with essential invoice fields
     - System validates input in real-time
     - System creates invoice in Reckon One via API
     - System converts Reckon invoice to UBL XML format
     - User can download or proceed with the generated UBL XML invoice

6. **PDF Invoice Data Extraction**
   - As a business owner, I want to upload PDF invoices so that the system can extract data and convert it to a standardized e-invoice.
   - Acceptance Criteria:
     - User can upload PDF invoices
     - System extracts data using OCR
     - User can review and correct extracted data
     - System generates UBL XML invoice

### Invoice Validation

7. **Validate UBL XML Invoice** (CORE)

   - As a user, I want to validate my UBL XML invoice against Australian standards so that I can ensure compliance before sending.
   - Acceptance Criteria:
     - User can upload or select a UBL XML invoice
     - System validates against wellformedness, syntax rules, PEPPOL rules, and schema
     - System displays validation results with clear error messages
     - User can see which specific rules were violated

8. **View Validation Report** (CORE)
   - As a user, I want to view a validation report so that I can understand and fix any issues with my UBL XML invoice.
   - Acceptance Criteria:
     - System displays validation errors with explanations
     - User can see which specific rules were violated
     - System provides basic suggestions for fixing errors
     - User can download the report in JSON format

### Invoice Sending

9. **Send Invoice via Email** (CORE)

   - As a user, I want to send my invoice via email using Reckon One API so that my client can receive it electronically.
   - Acceptance Criteria:
     - User can select a validated e-invoice
     - User can enter recipient email address
     - System sends the invoice via Reckon One email API
     - User receives confirmation of sending

10. **Send Invoice via PEPPOL** (IMPORTANT)
    - As a user, I want to send my UBL XML invoice via the PEPPOL network so that it can be delivered to recipients on the network.
    - Acceptance Criteria:
      - User can select a validated UBL XML invoice
      - User can enter recipient identifier
      - System sends the invoice to the PEPPOL network
      - User receives confirmation of sending

### Dashboard & Management

11. **View Invoice History** (CORE)

    - As a user, I want to view my invoice history so that I can track and manage my e-invoices.
    - Acceptance Criteria:
      - User can see a list of created/validated/sent invoices
      - User can filter invoices by status
      - User can view basic invoice details
      - User can download invoices in UBL XML format

12. **View API Documentation** (CORE)
    - As a user, I want to view documentation about the e-invoicing APIs so that I can understand how they work.
    - Acceptance Criteria:
      - User can access documentation for each API endpoint
      - Documentation includes request/response formats
      - Documentation includes authentication methods
      - Documentation includes example code snippets

## Future Enhancements (Post-MVP)

1. **PDF Invoice Data Extraction**

   - Extract data from PDF invoices using OCR techniques

2. **SFTP Sending Functionality**

   - Send invoices via SFTP protocol

3. **Advanced Validation Report**

   - Provide detailed fix suggestions for validation errors
   - Support multiple report formats (HTML, PDF)

4. **Advanced Dashboard Analytics**

   - Provide insights and analytics on invoice data
   - Generate reports on invoice status and trends

5. **Batch Processing**
   - Process multiple invoices in batch operations

## Development Analysis

### Core Features (Must-Have)

1. User authentication (registration, login)
2. Reckon One API integration
3. Invoice creation from CSV/Excel
4. Manual invoice creation form
5. UBL XML conversion
6. Invoice validation against Australian standards
7. Email sending functionality via Reckon One API
8. Basic PEPPOL network integration
9. Dashboard to view invoice history
10. API documentation

### Secondary Features (Nice-to-Have)

1. PDF invoice data extraction
2. SFTP sending functionality
3. Advanced validation report with fix suggestions
4. Multiple report formats (HTML, PDF)

### Development Considerations

1. **Technology Stack**

   - Frontend: React.js with ShadcnUI and tailwindCss
   - Backend: DotNet Web API
   - Database: MS-SQL
   - Authentication: Clerk

2. **API Integration**

   - Primary: Reckon One API for invoice creation and email sending
   - Secondary: ESS Validator for validation against Australian standards
   - Tertiary: Storecove API for PEPPOL network integration

3. **Development Timeline (6 weeks)**

   - Week 1: Project setup, authentication, and basic UI
   - Week 2: Reckon One API integration and invoice creation
   - Week 3: UBL XML conversion implementation
   - Week 4: Invoice validation integration
   - Week 5: Email and PEPPOL sending implementation
   - Week 6: Dashboard, testing, and bug fixes

4. **Scope Limitations**
   - Focus on demonstrating API endpoints rather than building a full production system
   - Limit the complexity of UBL XML conversion to essential fields
   - Implement basic PEPPOL integration without advanced features
   - Focus on JSON as the primary report format

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

- **Manual Invoice Form Page** - Form with required fields for manual invoice creation

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

- **Validation Results Page** - Display of validation results
  - Summary of validation status
  - Detailed error list with explanations
  - Basic fix suggestions
  - Download report option

### 5. Invoice Sending Pages

- **Email Sending Page** - Form to send invoice via email

  - Invoice selection
  - Recipient details
  - Email content customization
  - Send button

- **PEPPOL Sending Page** - Form to send invoice via PEPPOL
  - Invoice selection
  - Recipient identifier input
  - Send button

### 6. Management Pages

- **Invoice History Page** - List of all invoices with filtering

  - Sortable and filterable table of invoices
  - Basic search functionality
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

   - Ensure all pages work well on desktop and mobile devices
   - Prioritize important actions on smaller screens

3. **User Guidance**

   - Implement tooltips and help text for complex fields
   - Provide clear error messages and validation feedback
   - Include progress indicators for multi-step processes

4. **Accessibility**
   - Ensure proper contrast ratios for text
   - Include alt text for images
   - Support keyboard navigation

## Conclusion

This project will deliver a functional demonstration of e-invoicing APIs through a user-friendly GUI. By focusing on the core features of invoice creation with Reckon One API, UBL XML conversion, validation against Australian standards, and sending via email and PEPPOL, the application will provide SMEs with a reference implementation for e-invoicing solutions.

The development plan is designed to be achievable by a team of four (2 frontend, 2 backend) within a 6-week timeframe by prioritizing essential features and limiting scope to the most critical functionality. The user stories outlined above capture the core requirements while ensuring the project remains manageable within the given constraints.
