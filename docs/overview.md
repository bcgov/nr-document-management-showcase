---
title: Document Management Service  
description:  Store, update, index and retrieve attachments and documents.   
---   

## Summary
> The Document Management Service (DMS) provides the capability to store, update, index and retrieve attachments and documents. Access to the DMS is permitted for both IDIR and BCeID authenticated users. Permissions for documents stored in the DMS are controlled through Active Directory groups.

### Capabilities:

 * Share stored documents with multiple applications
 * Store multiple versions of documents, files and images
 * Assignment of rudimentary metadata to documents, files and images
 * Index and search documents, files and images
 * A mechanism to lock documents files that are identified as records

### Getting Started

[Developer Guide](https://www.github.com/bcgov/nr-document-management-showcase/readme.md) - Learn how to build your own application that connects to dms-api  
[DevHub](https://developer.gov.bc.ca)  
[DOMO](https://domo-master-jcyvmi-dev.pathfinder.gov.bc.ca) (Coming Soon) - A showcase app to help developers implement the DMS capabilities  
[DMOD](https://dmod.pathfinder.gov.bc.ca) - A showcase app done in 2018  (requires the dmod-user authorization in iauth.nrs.gov.bc.ca/int/adam)  

### Related GitHub Repositories
[nr-document-generation-showcase](https://github.com/bcgov/nr-document-generation-showcase)    
[nr-messaging-service-showcase](https://github.com/bcgov/nr-messaging-service-showcase)    
[nr-get-token](https://github.com/bcgov/nr-get-token)    
[csnr-dmod](https://github.com/bcgov/csnr-dmod)   

### Compatibility  

DMS File types supported include:   

``` pdf, doc, docx, xls, ppt, pptx, mpp, jpeg, gif, xml, kml, xsd, eml, txt, tiff, png, bmp, AutoCAD and msg ```

## Additional Resources

[The Open API definition for the DMS](https://apistore.nrs.gov.bc.ca/store/apis/info?provider=admin&version=v1&name=dms-api)  
[DMS Administration Guide](./admin-guide.md)  
[Documentation for the DMS API](https://apps.nrs.gov.bc.ca/int/confluence/display/DO/dms-api)  

**Legacy Documentation:**  
[DMS Administrator's Guide](https://apps.nrs.gov.bc.ca/int/confluence/pages/viewpage.action?pageId=14909703)   
