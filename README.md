﻿The European Medicines Verification System (EMVS) protects European citizens from falsified medicines by mandating the verification of every pack of prescription medicine at the point of dispense.  Verification is enabled by printing a unique identifier on the secondary packaging of each medicinal product.  The unique identifier is in the form of a two-dimensional Data Matrix ECC200 barcode containing a product code, serial number, batch (lot) identifier, expiry date and (in certain countries, only) an NHRN (National Healthcare Reimbursement Number).  
  
Most unique identifiers are formatted according to GS1 standards.  Data elements are identified using Application Identifiers (AIs). GTINs are used as product codes.  Some German medicines use ASCII MH10.8.2-based standards (IFA).  Data elements are identified using Data Identifiers (DIs). PPNs (Pharmacy Product Numbers) are used as product codes.  
  
The EMVS Unique Identifier Parser provides a reliable means of parsing the data reported to applications by barcode scanners.  The parser supports all legal barcode formats (GS1 FNC1, Format 05 (GS1) and Format 06 (IFA PPN)).  It correctly identifies AIs and DIs.  It validates each data element and reports any issues.  However, even if the data is invalid, it should still be submitted to the relevant National System.  The only exceptions are if there is clear evidence that the user has scanned an incorrect barcode (one that does not carry any unique identifier), or where there is no meaningful data to report to the National System.  The PackIdentifier object returned by the parser contains a Submit property which indicates if the parsed contents of the barcode should be submitted to the National System or not.  
  
The parser supports calibration using the Solidsoft Reply Barcode Scanner Calibrator.  When implemented in the context of a verification application, the calibrator provides data that the parser can use to ensure correct interpretation of the barcode data reported to it, even in situations where there are mismatches between the barcode scanner configuration and the OS keyboard layout.  The use of the calibrator ensures that parsing is highly reliable, eliminating the risk of generating ‘false positive’ alerts in the National System.  
  
The parser can be extended using pre-processor components.  Each preprocessor is a delegate which accepts an input string and returns the processed string.  Pre-processors are invoked sequentially, chaining the results of one pre-processor as the input of the next. Once all pre-processors have been invoked, the resulting string is parsed.