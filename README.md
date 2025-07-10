# Signatures-and-Imaging

The Signing and Imaging extension for Microsoft Dynamics 365 Business Central is a free offering from Braintree that allows you to record signatures against a document or take pictures and upload documents and store them with a link against any record.

The base version only implements the functionality in a select number of areas but it allows you to easily extend it into other areas of Business Central.

Features:
- Take pictures and upload documents
- Signing

## 1. Take Pictures and upload files

Out-of-the-box, this functionality is available for:
•	Warehouse Receipt Lines (Images are transferred to posted warehouse receipt lines on posting)
•	Posted Warehouse Receipt Lines
•	Warehouse Shipment Lines (Images are transferred to posted warehouse shipment lines on posting)
•	Posted Warehouse Shipment Lines

In Business Central, on the lines section for these documents, select the line you want to work with and use either of the options available. 


![Desktop](img\image.png)


![Mobile1](img\image-1.png) ![Mobile2](img\image-2.png)

> Note: Take Picture will only be available if a camera is detected by the Business Central client.

### 1.1 Extending

The Imaging Management BTR codeunit provides the following procedures to manage images related to a record.
- TakeNewPicture()
- UploadFile()
- OpenPictureList()

## 2. Signing

Out-of-the-box: available on:
- Posted Sales Shipment
- Posted Warehouse Shipment

Controls added to Shipment Headers:
![controls-exist](img\image-3.png)

Click on the No value in the signature field. System will prompt for signature:
![sign-desktop](img\image-4.png)

![sign-mobile](img\image-5.png)

Signature field will now show Yes. Clicking on the Yes value will open a preview to the page, from where you could delete the signature if required.

![updated-controls](img\image-6.png)

For the Posted Sales Shipment, the Customer Signature will reflect on the Certificate of Supply (be sure to select the custom layout at runtime or as your default layout on Report Layouts: 

![request-page](img\image-7.png)

![cert-of-supply](img\image-8.png)

### 2.1 Extending

In its simplest form, create an action that will call the `CaptureSignature()` procedure in the Signature Management BTR codeunit with the RecordId of the record you want to link the signature to.

Use the `GetSignature()` procedure to retrieve a record with the required signature. It has a field called Picture with **Type** = *Media*. This can be used to render the signature on pages or reports. 



> NOTE: Special care must be taken when handling signatures. This solution, as provided, does not allow exporting signatures outside the system. Extensions and custom implementations should only use signatures in association with their related records and solely for their intended business context. Braintree accepts no responsibility for any misuse, unauthorized access, or improper handling of signature data resulting from modifications or extensions to this functionality.

## 3. Troubleshooting
If you encounter any issues or errors while using the Signatures and Imaging extension please contact Braintree support, providing details such as error messages and the steps leading to the problem for efficient troubleshooting.

Email: bcsupport@braintree.co.za
