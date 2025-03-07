# E-Invoicing API Platform for SMEs - User Stories and Analysis

## Project Overview

This project aims to develop a web application that demonstrates e-invoicing API capabilities for Small and Medium Enterprises (SMEs) by leveraging the Reckon One API and supplementing it with additional services for Australian e-invoicing standards. The application will provide a user-friendly Website that demonstrates various e-invoicing API endpoints and their functions, focusing on three main categories:

1. **Invoice Creation** - Creating invoices via Reckon One API with automatic conversion to UBL XML format
2. **Invoice Validation** - Automatically validating UBL XML invoices against Australian e-invoicing standards
3. **Invoice Sending** - Transmitting validated invoices via email and PEPPOL network

The application will serve as a SaaS solution, allowing SMEs to create, validate, and send e-invoices without the need for expensive, inflexible vendor solutions that comply with Australian standards.

## Core Purpose

The core purpose of this application is to:

- Demonstrate the functionality of e-invoicing APIs through an intuitive GUI
- Show how Reckon One API can be integrated with UBL XML conversion for Australian standards
- Provide automated validation against Australian e-invoicing standards
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

4. **CSV/Excel to E-Invoice Conversion** (CORE)

   - As a business owner, I want to upload my CSV/Excel invoice data so that it can be automatically converted to a standardized e-invoice, validated, and prepared for sending.
   - Acceptance Criteria:
     - User can upload CSV/Excel files
     - System extracts invoice data
     - System creates invoice in Reckon One via API
     - System automatically converts Reckon invoice to UBL XML format
     - System automatically validates the UBL XML against Australian standards
     - User can view validation results and send the invoice if valid

5. **Manual Invoice Creation Form** (CORE)

   - As an accountant, I want to manually enter invoice details through a form so that I can create an invoice without existing digital data.
   - Acceptance Criteria:
     - User can fill out a form with essential invoice fields
     - System validates input in real-time
     - System creates invoice in Reckon One via API
     - System automatically converts Reckon invoice to UBL XML format
     - System automatically validates the UBL XML against Australian standards
     - User can view validation results and send the invoice if valid

6. **PDF Invoice Data Extraction** (FUTURE)
   - As a business owner, I want to upload PDF invoices so that the system can extract data and convert it to a standardized e-invoice.
   - Acceptance Criteria:
     - User can upload PDF invoices
     - System extracts data using OCR
     - User can review and correct extracted data
     - System generates UBL XML invoice

### Invoice Validation

7. **Automated UBL XML Invoice Validation** (CORE)

   - As a user, I want my UBL XML invoice to be automatically validated against Australian standards after creation so that I can ensure compliance before sending.
   - Acceptance Criteria:
     - System automatically validates newly created invoices
     - Validation checks wellformedness, syntax rules, PEPPOL rules, and schema
     - System displays validation results with clear error messages
     - User can see which specific rules were violated

8. **View Validation Report** (CORE)
   - As a user, I want to view a validation report so that I can understand and fix any issues with my UBL XML invoice.
   - Acceptance Criteria:
     - System displays validation status (success or failure)
     - For failed validations, system shows errors with explanations
     - User can see which specific rules were violated
     - System provides basic suggestions for fixing errors

### Invoice Sending

9. **Send Invoice via Email** (CORE)

   - As a user, I want to send my validated invoice via email so that my client can receive it electronically.
   - Acceptance Criteria:
     - User can send a validated e-invoice directly from the validation results page
     - User can enter recipient email address
     - System sends the invoice with PDF and UBL XML attachments
     - User receives confirmation of sending

10. **Send Invoice via PEPPOL** (IMPORTANT)
    - As a user, I want to send my validated UBL XML invoice via the PEPPOL network so that it can be delivered to recipients on the network.
    - Acceptance Criteria:
      - User can send a validated UBL XML invoice directly from the validation results page
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
      - User can download invoices in UBL XML and PDF formats

12. **View Invoice Details** (CORE)

    - As a user, I want to view detailed information about a specific invoice so that I can review its contents and status.
    - Acceptance Criteria:
      - User can see all invoice details including line items
      - User can see validation status and sending status
      - User can download the invoice in UBL XML and PDF formats
      - User can resend the invoice if needed

13. **View API Documentation** (CORE)
    - As a user, I want to view documentation about the e-invoicing APIs so that I can understand how they work.
    - Acceptance Criteria:
      - User can access comprehensive documentation for the business process flow
      - Documentation includes API integration steps
      - Documentation includes UBL conversion details
      - Documentation includes validation and sending processes

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
5. Automated UBL XML conversion
6. Automated invoice validation against Australian standards
7. Email sending functionality
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

Based on the latest design and automated workflow, the following pages will be needed:

### 1. Authentication Pages

- **Landing Page** - Introduction to the platform with login/register options
- **Registration Page** - Form for new users to create an account
- **Login Page** - Form for existing users to log in
- **Password Reset Page** - Form to request and process password resets

### 2. Dashboard Pages

- **Main Dashboard** - Overview of recent activity, quick access to main functions
  - Summary statistics (invoices created, validated, sent)
  - Recent invoices with status indicators
  - Quick action button for creating new invoices

### 3. Invoice Creation Pages

- **CSV/Excel Upload Page** - Interface for uploading CSV/Excel files

  - File upload area
  - Processing indicator
  - Direct creation without preview step

- **Manual Invoice Form Page** - Form with required fields for manual invoice creation
  - Structured form with sections for:
    - Seller details
    - Buyer details
    - Invoice details (date, number, etc.)
    - Line items
    - Tax information
    - Payment terms
  - Real-time validation
  - Direct submission for processing

### 4. Processing and Validation Pages

- **Processing Page** - Shows the automated workflow in progress

  - Progress indicators for each step:
    - Invoice creation in Reckon One
    - UBL XML conversion
    - Validation against Australian standards
  - Automatic transition to validation results

- **Validation Results Page** - Display of validation results
  - Summary of validation status
  - UBL XML preview
  - For successful validations:
    - Option to send via email
    - Option to send via PEPPOL
  - For failed validations:
    - Detailed error list with explanations
    - Option to go back and fix issues

### 5. Management Pages

- **Invoice History Page** - List of all invoices with filtering

  - Sortable and filterable table of invoices
  - Status indicators (Created, Validated, Sent, Failed)
  - Action buttons (view, download, send)

- **Invoice Detail Page** - Detailed view of a specific invoice

  - Complete invoice information
  - Line items table
  - Status information
  - UBL XML preview
  - Action buttons (download, resend)

- **API Documentation Page** - Documentation for the e-invoicing process
  - Business process flow
  - API integration steps
  - UBL conversion details
  - Validation and sending processes
  - SME guidelines

### 6. Error Pages

- **404 Page** - Custom page for not found errors
  - Clear error message
  - Navigation options to key pages
  - Popular pages links

### Page Flow Diagram

The user journey through these pages would typically follow this streamlined flow:

1. User registers/logs in → Dashboard
2. From Dashboard:
   - Create Invoice → Choose Method (Manual Form or CSV Upload) → Processing → Validation Results → Send Invoice (if valid)
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
   - Include progress indicators for automated processes

4. **Accessibility**
   - Ensure proper contrast ratios for text
   - Include alt text for images
   - Support keyboard navigation

## Conclusion

This project will deliver a functional demonstration of e-invoicing APIs through a user-friendly GUI with an automated workflow. By focusing on the core features of invoice creation with Reckon One API, automatic UBL XML conversion, validation against Australian standards, and sending via email and PEPPOL, the application will provide SMEs with a streamlined e-invoicing solution.

The updated design emphasizes automation and simplicity, reducing the number of steps required to create, validate, and send e-invoices. This approach not only improves the user experience but also reduces the potential for errors in the e-invoicing process.
