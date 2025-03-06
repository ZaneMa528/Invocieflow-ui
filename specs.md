
In  2014,  the  European  Commission  declared UBL  2.1  was  officially  eligible  for  referencing  in 
tenders from public administrations (one of the first non-European standards to be so recognized). 
It is expected that the adoption of UBL as a standard message representation will increase as it 
defines  a  royalty-free  library  of  standard  XML  business  documents  that  not  only  supports 
invoicing  but  also  all  other  aspects  related  to  the  digitization  of  the  commercial  and  logistical 
processes for domestic and international supply chains (e.g. procurement, purchasing, transport, 
logistics, intermodal freight management). 
In addition to data and messaging standards, there are multiple alternatives for  communication 
methods  like  email  or  secure  File  Transfer  Protocol  (SFTP).  Peppol  is  a  set  of  artifacts  and 
technical specifications that facilitates easy data  exchange across disparate government systems 
and  their  suppliers.  Many  EU  countries  have  adopted  Peppol  as  a  communication  method 
including  Belgium,  Croatia,  Cyprus,  Denmark,  Greece,  Ireland,  Latvia,  Lithuania,  Luxemburg, 
Malta, Norway, Poland, and SloveniPEPPOL’s most recent usage statistics can be accessed at 
PEPPOL statistics (ionite.net). 
In  Australia,  all  New  South  Wales  state  government  agencies  will  have  to  use  e-invoicing  for 
goods  and  services  valued  at  up  to  AUD  1  million  from  2022.  It  is  expected  that  this  will  be 
extended  to  SMEs  in  the  longer  term  so  a  solution  that  is  flexible  to  use  is  needed.  Existing 
solutions present difficulties when adopted by SMEs: 
• Cost 
• Flexibility 
• Vendor dependence 
Therefore, SMEs need a cost-effective solution that is both open and flexible. This way, they can 
better leverage their existing assets, use components from different vendors and be in control of 
the evolution of their e-invoicing solutions. 
Towards a SaaS e-invoicing ecosystem for Australia 
What is Software-as-a-Service (SaaS)? 
Software  as a Service (SaaS) is a concept that pushes software  away  from local computers into 
Web services. This means users no longer buy software to install locally but instead buy the right 
to  use  the  software  over  the  Internet.  SaaS  providers  maintain  the  hardware,  perform  upgrades, 
backup your data (sometimes), and otherwise perform all of the “keep the lights on” services and 
activities required to keep the software running. [1] 
The purpose of the project is to introduce students to the concept of SaaS by considering each team 
as a company that performs the following: 
1. The company creates a software product (referred to as a  service as it is accessible via a 
REST API) and hosts it on a cloud server. 
2. Customers can subscribe to the service as soon as it is operational, giving feedback to the 
company 
3. The  company  makes  both  major  and  minor  updates  to  the  software,  and  the  customers 
automatically get those updates as part of their subscriptions. 
We  will  only  be  concerned  with  the  technical  aspects  of  SaaS  in  this  project  (the  building  and 
deployment of the software product) rather than other aspects like charging etc. 
All software services that will be built by the teams will be around creating a SaaS e-invoicing 
ecosystem for Australia. 
[1] Software as a Service Vs. Software as a Product - Pragmatic Institute 
Ecosystem description 
An  ecosystem  of  services  consists  of  SaaS  services  that  can  be  composed,  configured  and 
customised  according  to  different  contexts  in  accordance  with  Service-Oriented  Architecture 
(SOA) and Business Process Modelling (BPM) principles. Each service is providing a particular 
functionality  in  the-invoicing  services  ecosystem,  can  potentially  be  provided  by  a  different 
vendor, is available via an API and is available on a pay-by-use basis. Companies (and in particular 
SMEs) can create flexible, open and multi-vendor solutions in the form of e-invoicing workflows 
that enforce business document exchange processes that are applicable in a certain context. 
The categories of services in the ecosystem are listed in the following table: 
SaaS Category Description Customization Points 
Invoice Creation Creates a standardised einvoice from 
an existing information system 
Supports different input formats: 
• Convert from a text file 
(CSV or Excel) 
• Read from SQL Tables 
• EXtract data from PDF 
Invoice (image) 
• Ask user to fill a GUI Form 
Invoice Validation 
Creates a report outlining any 
validation errors according to 
Australian rules 
Supports the generation of 
validation reports in different 
formats: 
• JSON 
• HTML 
• PDF 
Invoice 
Sending/Receiving 
Sends the electronic invoice to a 
number of recipients. Can fail if there 
is a communication error. 
Receives an electronic invoice from a 
mailbox. 
Supports  the  sending  of  electronic 
invoices using different protocols: 
• Email 
• SFTP 
Supports the generation of 
communication reports in different 
formats: 
• JSON 
• HTML 
• PDF 
Standardised electronic invoices 
A rising international standard for representing e-invoices is the UBL XML standard which has 
been  adopted  in  Australia.  UBL  was  originally  introduced  in  2003,  as  an  open,  extensible,  and 
customizable XML document for business. In September 2008, European stakeholders in public 
and government created the Pan-European Public Procurement On-line (PEPPOL) project. With 
UBL  formatted  XML  invoices,  it  is  possible  to  record  business  transactions  from  supplier  to 
transportation,  and  finally  to  the  buyer.  In  this  context,  we  assume  all  standardised  electronic 
invoices are in XML format. An example is shown in the diagram below: 
 
There  are  slight  variations  between  the  different  UBL  invoices  according  to  countries.  In  this 
context, we use Australia’s UBL specifications available at: 
• https://softwaredevelopers.ato.gov.au/sites/default/files/resource-
attachments/A_NZ_Invoice_specification_tracked_v1.0.docx 
• https://github.com/A-NZ-PEPPOL/A-NZ-PEPPOL-BIS-3.0 
We are only considering Commercial Invoice (type 380) so other types can be ignored. 
Introducing UBL XML format 
What is UBL? 
Defined by OASIS Open, UBL, the Universal Business Language, defines a royalty-free library 
of standard XML business documents supporting the digitization of the commercial and logistical 
processes for domestic and international supply chains such as procurement, purchasing, transport, 
logistics, intermodal freight management, and other supply chain management functions. UBL has 
also become foundational to a number of efforts in the transport and logistics domain, including 
the  European  Common  Framework  (European  Commission),  DTTN  (Port  of  Hong  Kong), 
TradeNet (Port of Singapore), Electronic  Freight Management (US), and Freightgate (globally). 
In  2014  the  European  Commission  declared UBL  2.1  was  officially  eligible  for  referencing  in 
tenders from public administrations (one of the first non-European standards to be so recognized). 
In this document, we are only interested in describing the UBL XML standard and in particular 
the representation of electronic invoices in the Australian context. Such electronic invoices have 
these characteristics: 
• Each core element of an e-invoice is part of the EN16931 semantic data model, established 
as a European Standard. EN16931 includes only the essential information that an e-invoice 
needs to ensure legal compliance. 
• The syntax of the UBL document must be compliant with the UBL schema 
• Each country can “customise“ the standard according to its own requirements. 
More information about UBL XML can be found here 
https://www.xml.com/articles/2017/01/01/what-is-ubl/ 
Example of a UBL Invoice 
The figure below is a subsection of the UBL invoice where each number on the image represents: 
1. Invoice type code 380 indicates it is an invoice. 
2. The charge amount is negative to correct the original invoice. 
3. All document-level (LegalMonetaryTotal) amounts are negative. 
4. Start of invoice line 1. 
5. The price amount must always be positive and is not changed. 
6. Start of invoice line 2. 
 
Australia/NZ UBL Specifications 
This course will use the specific requirements for Australia and New Zealand. Material related to 
the specs can be found in https://github.com/A-NZ-PEPPOL/A-NZ-PEPPOL-BIS-3.0. 
For example, samples can be accessed from this folder https://github.com/A-NZ-PEPPOL/A-NZ-
PEPPOL-BIS-3.0/tree/master/Message%20examples 
Australian E-invoice Examples 
Two examples are provided: 
Example 1: Simple/minimal UBL XML invoice example1.xml 
Example 2: More complete example, available from the ATO GitHub repository AU Invoice.xml 
The  following  spreadsheet  gives  the  correspondence  between  the  tags  and  the  values  in  both 
examples: 
https://docs.google.com/spreadsheets/d/12tn0g5ri40iLO2vLLLKjviSDPAs81swIiEASVbN4MtE
/edit?usp=sharing 
Ecosystem summary 
The figure below summarises all API categories in the ecosystem, however only three categories 
are covered in this project i.e. E-invoice creation, E-invoice validation and E-invoice sending. A 
brief description of API inputs, outputs, functionality are described below: 
 
Invoice Creation 
Only standardised data can be processed by other categories of services. To reduce the barrier for 
customers to use the system, the customer should be able to convert data from their current system 
to standard e-invoices in batches. 
For this category, your service should be able to create standardised e-invoices from an existing 
information system or allow information to be imported from external sources. Although you are 
not  expected  to  be  able  to  extract  information  from  a  random  source  like  websites  or  articles, 
services in this category should be able to process pre-formatted data. The service should extract 
any useful data from the source and assemble invoices as per the standard. 
Input 
Below are some possible approaches for creating an invoice, the implementation of your service 
can support some of them, or even something not on the list. 
• Convert from a text file: you can assume the data of the invoice is contained in a text file 
(CSV or Excel) 
• Read from a database: you can assume the invoice data is in SQL Tables 
• Extract data from an image: you can assume you are reading invoice data from a PDF 
• Ask user to fill a GUI Form 
You  should  define  the  parameters  required  by  your  service.  You  may  define  optional  and 
compulsory fields, but more compulsory fields generally mean you will handle fewer exceptions 
in the service but reduce the usability and generality of the service. 
Output 
Your output should conform to the UBL 2.1 XML format. i.e. Your output should be able to pass 
any  correctly  implemented  validator  mentioned  in  the  “Invoice  Validation”  section  of  this 
document.  Since  there  are  many  fields  and  constraints  in  the  standard,  a  microservice  should 
consider starting by generating minimised invoices first. 
Possible APIs that can be used to implement the service 
• https://upbrainsai.com/ API if to extract data from an invoice image or PDF. 
• There are several APIs such as Invoice Data Extraction in RAPID API that can extract 
data from an invoice using OCR techniques. 
Invoice Validation 
Creates  a  report  outlining  any  validation  errors  according  to  Australian  rules.  ATO  maintains  a 
GitHub repository with all the specifications at https://github.com/A-NZ-PEPPOL/A-NZ-
PEPPOL-BIS-3.0/tree/master/Specifications 
Latest  Details  of  Validation  rules  can  be  found  in  Appendix  A  and  B  of  the  document 
“Specifications/A-NZ_Invoice_Extension_versionX.docx” in the ATO GitHub repository 
In order to maintain an efficient system, it is essential that the invoices are validated based on the 
rules employed by a governing entity. The validation system aids to detect and rectify errors before 
a payment is initiated. 
The validation microservice has four components: 
• Validating  Wellformedness  (Checking  if  the  input  is  valid  and  the  file  itself  has  valid 
contents) 
• Syntax Rules (Validates EN16931 business rules) (Appendix B, BR Rules) 
• PEPPOL rules (Validates Specific AUNZ business rules) (Appendix B, PEPPOL Rules) 
• Schema Validation (Validates the schema of the invoice 
Note: Schema rules are rules concerning what tags are allowed in the UBL XML file. For example 
tag cac:BillingReference is a valid tag and tag <cac:sydney> is invalid. It also specifies how the 
tags are sequenced. Schema rules are contained in an XSD file. In this case, the UBL XSD file is 
downloadable  at:  https://docs.oasis-open.org/ubl/os-UBL-2.1/xsd/maindoc/UBL-Invoice-2.1.xsd 
(you may need to copy the path as it may not connect directly) To validate an XML file, you need 
to find a library that does schema validation in your programming language. 
Input 
The input to this microservice will be a UBL 2.1 XML format invoice. 
Output 
The output of this microservice should: 
1. Be in a machine-readable format (i.e. JSON, HTML, PDF) 
2. Indicate which validation rules are violated. 
3. Provide additional information on why the rule was violated. 
4. *Optional* Suggest quick-fix methods to validate the rules. 
Possible APIs that can be used to implement the service 
• ESS Validator (for details contact Muhammad Raheel Raza 
muhammad_raheel.raza@unsw.edu.au). A guide to ESS Validator is in the given PDF ESS 
Validate API - Developer Guide 2- Google Docs.pdf 
• ECOSIO validator: https://ecosio.com/en/peppol-and-xml-document-validator/ 
Invoice Sending/Receiving 
After invoices are generated, the system needs a way to distribute the invoices to corresponding 
recipients. This category of services should be able to deliver invoices from the internal system to 
some external environment. You need to design the way how invoices are delivered. Some possible 
ways can be email, SFTP or even SMS. 
Input 
Input will conform to the UBL format in the recommended format. (i.e., The input should be able 
to pass the validator mentioned in the “Invoice Validation” section). But you should consider and 
define how your service takes the input. 
Output 
The observable output of this service includes a report and a side effect. After the API call, your 
service should send the invoice and then return a communication report. The format of the report 
can  be  but  is  not  limited  to  JSON,  HTML,  and  PDF.  If  there  is  any  communication  error.  it  is 
preferable  that  your  service  reacts  with  a  human-readable  message.  A  simple  synchronous  API 
call without delivering information to  external is acceptable as a start, but not sufficient for the 
service. Similar is the case for Receiving scenario.  
Possible APIs that can be used to implement the service 
Storecove API can be used https://www.storecove.com/au/en/ (if PEPPOL network is selected).