# Reckon One API Analysis for E-Invoicing Project

## Overview

Reckon One is an accounting software platform that provides API capabilities for various accounting functions, including invoicing. This document analyzes how the Reckon One API can be integrated with our e-invoicing platform for SMEs.

## Detailed API Structure

Based on the Swagger documentation (https://api-v2.reckonone.com/swagger/index.html?url=/swagger.json#/Invoices), the Reckon One API provides comprehensive endpoints for invoice management. Below is a detailed breakdown of the relevant endpoints and their structures.

### Invoice Endpoints

#### Invoice Creation and Management

- **POST /api/v2/invoices** - Create a new invoice

  - Request Body: `InvoiceDto` object containing:
    - `customerId` (required): Customer ID
    - `invoiceNumber` (required): Invoice number
    - `reference`: Reference number
    - `issueDate` (required): Date invoice was issued
    - `dueDate` (required): Date payment is due
    - `lines` (required): Array of invoice line items
    - `status`: Invoice status (Draft, Approved, etc.)
    - `currencyCode`: Currency code (default: AUD)
    - `exchangeRate`: Exchange rate for foreign currencies
    - `notes`: Additional notes
    - `terms`: Payment terms
    - `taxInclusive`: Whether amounts include tax
  - Response: Created `InvoiceDto` with ID

- **GET /api/v2/invoices** - List all invoices

  - Query Parameters:
    - `pageNumber`: Page number (default: 1)
    - `pageSize`: Page size (default: 100)
    - `sortBy`: Field to sort by
    - `sortDirection`: Sort direction (Ascending/Descending)
    - `status`: Filter by status
    - `customerId`: Filter by customer
    - `fromDate`/`toDate`: Date range filters
  - Response: Paged list of `InvoiceDto` objects

- **GET /api/v2/invoices/{id}** - Get a specific invoice

  - Path Parameters:
    - `id`: Invoice ID
  - Response: `InvoiceDto` object

- **PUT /api/v2/invoices/{id}** - Update an invoice

  - Path Parameters:
    - `id`: Invoice ID
  - Request Body: `InvoiceDto` object
  - Response: Updated `InvoiceDto`

- **DELETE /api/v2/invoices/{id}** - Delete an invoice
  - Path Parameters:
    - `id`: Invoice ID
  - Response: Success status

#### Invoice Line Items

- **POST /api/v2/invoices/{invoiceId}/lines** - Add a line item to an invoice

  - Path Parameters:
    - `invoiceId`: Invoice ID
  - Request Body: `InvoiceLineDto` containing:
    - `description` (required): Line item description
    - `quantity` (required): Quantity
    - `unitPrice` (required): Price per unit
    - `accountId`: Account ID for the line
    - `taxRateId`: Tax rate ID
    - `discount`: Discount percentage
  - Response: Created `InvoiceLineDto` with ID

- **PUT /api/v2/invoices/{invoiceId}/lines/{id}** - Update a line item

  - Path Parameters:
    - `invoiceId`: Invoice ID
    - `id`: Line item ID
  - Request Body: `InvoiceLineDto`
  - Response: Updated `InvoiceLineDto`

- **DELETE /api/v2/invoices/{invoiceId}/lines/{id}** - Delete a line item
  - Path Parameters:
    - `invoiceId`: Invoice ID
    - `id`: Line item ID
  - Response: Success status

#### Invoice Actions

- **POST /api/v2/invoices/{id}/approve** - Approve an invoice

  - Path Parameters:
    - `id`: Invoice ID
  - Response: Updated `InvoiceDto`

- **POST /api/v2/invoices/{id}/email** - Send invoice via email

  - Path Parameters:
    - `id`: Invoice ID
  - Request Body: `EmailInvoiceDto` containing:
    - `to` (required): Recipient email addresses
    - `cc`: CC email addresses
    - `bcc`: BCC email addresses
    - `subject`: Email subject
    - `body`: Email body
    - `attachPdf`: Whether to attach PDF (default: true)
  - Response: Success status

- **GET /api/v2/invoices/{id}/pdf** - Generate PDF version of invoice
  - Path Parameters:
    - `id`: Invoice ID
  - Query Parameters:
    - `template`: Template name (optional)
  - Response: PDF file stream

#### Invoice Templates

- **GET /api/v2/invoices/templates** - Get invoice templates
  - Response: Array of template names and descriptions

#### Invoice Import/Export

- **POST /api/v2/invoices/import** - Import invoices from external formats

  - Request Body: `ImportInvoicesDto` containing:
    - `format` (required): Format type (CSV, Excel, etc.)
    - `file` (required): Base64 encoded file content
    - `mappings`: Column mappings
  - Response: Import results with success/failure counts

- **GET /api/v2/invoices/export** - Export invoices to external formats
  - Query Parameters:
    - `format`: Export format (CSV, Excel, etc.)
    - `fromDate`/`toDate`: Date range filters
    - `status`: Filter by status
  - Response: File stream in requested format

### Customer Endpoints Relevant to Invoicing

- **GET /api/v2/customers** - List all customers

  - Query Parameters: Similar pagination and filtering options
  - Response: Paged list of `CustomerDto` objects

- **GET /api/v2/customers/{id}** - Get a specific customer
  - Path Parameters:
    - `id`: Customer ID
  - Response: `CustomerDto` containing:
    - `id`: Customer ID
    - `name`: Customer name
    - `email`: Email address
    - `phone`: Phone number
    - `addresses`: Billing/shipping addresses
    - `taxNumber`: Tax registration number
    - `currencyCode`: Preferred currency
    - `paymentTerms`: Default payment terms

### Tax Rate Endpoints Relevant to Invoicing

- **GET /api/v2/taxRates** - List all tax rates
  - Response: Array of `TaxRateDto` objects containing:
    - `id`: Tax rate ID
    - `name`: Tax rate name
    - `rate`: Percentage rate
    - `code`: Tax code

## Data Models

### Key Data Structures

1. **InvoiceDto**

   ```json
   {
     "id": "string",
     "businessId": "string",
     "customerId": "string",
     "customerName": "string",
     "invoiceNumber": "string",
     "reference": "string",
     "issueDate": "2023-07-15T00:00:00Z",
     "dueDate": "2023-08-15T00:00:00Z",
     "status": "Draft",
     "currencyCode": "AUD",
     "exchangeRate": 1.0,
     "subtotal": 0.0,
     "taxAmount": 0.0,
     "total": 0.0,
     "amountPaid": 0.0,
     "amountDue": 0.0,
     "notes": "string",
     "terms": "string",
     "taxInclusive": true,
     "lines": [
       {
         "id": "string",
         "description": "string",
         "quantity": 1.0,
         "unitPrice": 100.0,
         "discount": 0.0,
         "accountId": "string",
         "taxRateId": "string",
         "taxRate": 10.0,
         "subtotal": 100.0,
         "taxAmount": 10.0,
         "total": 110.0
       }
     ]
   }
   ```

2. **CustomerDto**
   ```json
   {
     "id": "string",
     "businessId": "string",
     "name": "string",
     "firstName": "string",
     "lastName": "string",
     "email": "string",
     "phone": "string",
     "mobile": "string",
     "fax": "string",
     "website": "string",
     "billingAddress": {
       "line1": "string",
       "line2": "string",
       "city": "string",
       "state": "string",
       "postalCode": "string",
       "country": "string"
     },
     "shippingAddress": {
       "line1": "string",
       "line2": "string",
       "city": "string",
       "state": "string",
       "postalCode": "string",
       "country": "string"
     },
     "taxNumber": "string",
     "currencyCode": "AUD",
     "paymentTerms": "string",
     "notes": "string"
   }
   ```

## Integration Analysis for Our E-Invoicing Project

### Strengths

1. **Complete Invoice Lifecycle** - Reckon One API covers the entire invoice lifecycle from creation to sending
2. **PDF Generation** - Built-in capability to generate PDF invoices
3. **Email Functionality** - Direct API for sending invoices via email
4. **Customer Management** - APIs for managing customer data needed for invoices
5. **Authentication** - Secure token-based authentication system
6. **Flexible Filtering** - Comprehensive filtering options for invoice queries
7. **Template Support** - Support for different invoice templates

### Limitations

1. **UBL XML Format** - No direct support for UBL XML format required by Australian e-invoicing standards
2. **Validation** - No specific endpoints for validating invoices against Australian e-invoicing standards
3. **PEPPOL Network** - No direct PEPPOL network integration
4. **SFTP Sending** - No direct SFTP sending capabilities
5. **Limited Export Formats** - Export formats may not include UBL XML

## Mapping to Our Project Requirements

### Invoice Creation

| Our Requirement             | Reckon One API Support           | Gap Analysis                |
| --------------------------- | -------------------------------- | --------------------------- |
| CSV/Excel to E-Invoice      | Supported via `/invoices/import` | Needs conversion to UBL XML |
| Manual Invoice Creation     | Supported via `/invoices` POST   | Needs conversion to UBL XML |
| PDF Invoice Data Extraction | Not directly supported           | Need custom implementation  |

### Invoice Validation

| Our Requirement        | Reckon One API Support | Gap Analysis                        |
| ---------------------- | ---------------------- | ----------------------------------- |
| Validate E-Invoice     | Not supported          | Need integration with ESS Validator |
| View Validation Report | Not supported          | Need custom implementation          |

### Invoice Sending

| Our Requirement          | Reckon One API Support               | Gap Analysis                              |
| ------------------------ | ------------------------------------ | ----------------------------------------- |
| Send E-Invoice via Email | Supported via `/invoices/{id}/email` | No gaps                                   |
| Send E-Invoice via SFTP  | Not supported                        | Need custom implementation                |
| Send via PEPPOL          | Not supported                        | Need integration with PEPPOL access point |

## Integration Strategy

### Primary Integration Points

1. **Invoice Creation**

   - Use Reckon One's invoice creation APIs to generate invoices
   - Implement a conversion layer to transform Reckon's invoice format to UBL XML

2. **Customer Data**

   - Leverage Reckon's customer APIs to maintain consistent customer information
   - Map customer data to UBL XML party information

3. **Email Sending**
   - Utilize Reckon's email functionality for sending invoices
   - Add options to include UBL XML as attachment

### Supplementary Services Needed

1. **UBL XML Conversion Service**

   - Develop a service that maps Reckon's `InvoiceDto` to UBL XML format
   - Implement validation against UBL schema

2. **Invoice Validation Service**

   - Integrate with ESS Validator or similar service for Australian standards validation
   - Implement a validation report viewer

3. **PEPPOL Network Integration**

   - Integrate with a PEPPOL access point provider (e.g., Storecove)
   - Implement sending of UBL XML invoices to the PEPPOL network

4. **SFTP Sending Service**
   - Implement custom SFTP sending functionality
   - Add security features for SFTP credentials management

## API Authentication and Security

Reckon One uses OAuth 2.0 token-based authentication:

1. Applications must register and obtain client credentials
2. Authentication tokens must be included in all API requests as Bearer tokens
3. Tokens expire and need to be refreshed periodically using the refresh token endpoint

## Implementation Recommendations

1. **Phased Approach**

   - Phase 1: Basic invoice creation and management using Reckon APIs
   - Phase 2: Add UBL XML conversion and validation
   - Phase 3: Implement advanced sending options (PEPPOL, SFTP)

2. **API Wrapper**

   - Create a service layer that abstracts Reckon API calls
   - Handle authentication token management
   - Implement error handling and retry logic

3. **Caching Strategy**

   - Cache customer data and templates to reduce API calls
   - Implement efficient token refresh mechanism

4. **Testing Strategy**
   - Create test accounts in Reckon One
   - Develop comprehensive integration tests
   - Validate UBL XML output against Australian standards

## Conclusion

The Reckon One API provides a solid foundation for basic invoicing functionality but will need to be supplemented with additional services to fully support Australian e-invoicing standards and the PEPPOL network. A hybrid approach using Reckon's APIs for core functionality and custom implementations for e-invoicing specific requirements is recommended.

Our project will need to focus on building the conversion layer between Reckon's invoice format and UBL XML, as well as integrating with validation services and PEPPOL access points. The email sending functionality can leverage Reckon's existing capabilities, while SFTP sending will require custom implementation.
