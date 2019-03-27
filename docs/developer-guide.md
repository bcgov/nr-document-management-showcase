# DMS Developer’s Guide

The Document Management System (DMS) can store a variety of objects including documents, spreadsheets, images, videos and shape files. The DMS can only be accessed programmatically via the DMS-API. A description of the DMS-API can be found in [NRM API Store](https://apistore.nrs.gov.bc.ca/store/apis/info?name=dms-api&version=v1&provider=admin).

The DMS-API is secured using OAuth2 security. Anonymous access to the DMS-API is not permitted. Users of the DMS-API must have OAuth2 scopes for both the DMS-API and the DMS itself in order to access the DMS repository via the API.

## Capabilities

The DMS API provides the capability to store and retrieve non-structured data as well as supporting full-text searching and indexing of both metadata and data contents. The following is a list of resources exposed by this API:

-   Files: Files are stored in the DMS along with associated metadata.  The maximum size of files stored in the DMS repository is determined by a configurable parameter within WCC.
-   File Metadata: Each file is stored along with related metadata to help identify the file. The API supports metadata retrieval, including file size, author, records classification number and security classification.
-   File Versions: Each time a file is updated via the API, a new version of the file is created.
-   File Search: The API supports searching for files using keywords. Full-text searches are also supported.
-   File Check-out: retrieves the latest version of the file from the DMS. Once checked-out for editting, the version of the file stored in the DMS is locked against further updates until the file is checked-in.
-   Folders: Folders are used to organize and secure files within the DMS. The DMS supports both static folders and dynamically created folders. The top level folders are implemented as static folders in order to ensure consistency of the folder hierarchy within the DMS. Sub-folder can be created dynamically for the specific needs of individual business areas.
-   Links: A link is a shortcut to a file that resides in another folder.

## Security


**DMS Security**

Security within the DMS is provided through role-based access control (RBAC) configured through WebADE. WebADE roles for the DMS include DMS.READ_ONLY, DMS.READ_WRITE, DMS.STAFF_USER, and DMS.CLIENT_USER. In addition, DMS access should also be limited by business area using a role defined in WebADE. Role-based access is set at the folder level by the WCC administrator during the initial set-up of WCC for a specified business area.

**DMS API Security**

 In order to use the DMS-API, a WebADE service client must first be defined (e.g. APP_CLIENT). Next, permission to use the DMS-API must be set within WebADE. The WebADE role DMS.CONTRIBUTOR is employed to secure the DMS-API's generic endpoints. 

When a valid OAuth2 token is returned for the DMS-API, the OAuth2 scopes in the token are checked. Access to documents is only permitted if the required authorizations in the DMS have been implemented. The OAuth client accessing the DMS-API must have a scope that allows access to the DMS-API (e.g. DMS.\*).

## Folder Structure

The DMS folder hierarchy structure consists of upper level folders that are static and lower level folders that are dynamic. Dynamic folders can be modified to suit the needs of line-of-business clients that have been registered to use the DMS.

The top level folders in the DMs folder hierarchy are called Root folders.  Not all Root folders are visible using the DMS-API. These folders cannot be edited.

The folders visible through the DMS-API include:

-   NRS: to store all documents related to NRS systems and LOBs

-   DG_TEMPLATES: to store documents used by the DG API

-   NRSOS: for use by the NRS Online Services portal.

The second level folders in the DMS are called Source System folders. Line-of-business specific folders are configured at this level.

The third level folders in the DMS are called Engagement Folders. Engagement folders are currently used only by NRSOS (NRPP). One engagement folder is created under NRS/NRSOS for each new permit application. All files stored in and engagement folder will have the same security permissions and will share the same metadata.

![](C:\Temp\DMS_Folder_Structure.jpg)

Figure 1- DMS Folder Structure

## Getting Started

**Business Activities**

1. Define a business area specific hierarchy for storing documents
2. Ensure that the document storage hierarchy aligns with ARC/ORCS classifications
3. Define mandatory metadata for top-level folders; subfolders inherit metadata from the parent folder
4. Define mandatory security for top-level folders; subfolders inherit security from the parent folder

**Technical Activities**

The technical activities detailed below are executed using two different  software utilities. Roles are created in WebADE using the [ADaM](http://www.webade.org/adamWhatIs.html) graphical user interface. Folders are populated in [WebCenter Content](https://www.oracle.com/technetwork/middleware/webcenter/content/overview/index.html) (WCC) using the command-level interface.  WCC is a commercial product from Oracle that provides document and records management services that underly the DMS.

1. Create roles in WebADE, or reuse existing roles, to implement security requirements defined by the business area
2. Create a second level folder for a specific business area in WCC
3. In WCC, assign roles and metadata to the second level (business area specific folder
4. Create subfolders as necessary in WCC; subfolder inherit roles and metadata from the parent folder
5. Add additional roles and/or metadata to the subfolders if required

