<!-- loio9d96aae577f845708b53ebd18dab3745 -->

# Export Change Logs with a History of Administration Operations

You can download a CSV file with a history of the operations performed by administrators in the administration console for SAP Cloud Identity Services.



## Context

The exported change logs are saved in a CSV file and contain information about *CREATE*, *UPDATE*, or *DELETE* operations performed by administrators. The change logs are stored in the data base for 24 months.

Each record should contain the following data:

-   *Date*

    The date when the resource was created, updated, or deleted.

-   *Administrator's ID*

    The ID of the user or the system that made the change.

-   *Administrator's Name*

    The name of the user or the system that made the change.

-   *Resource Type*

    This indicates which type of resource was created, updated, or deleted, for example service provider.

-   *Resource ID*

    An identifier for the resource.

-   *Resource Name*

    The name of the resource that was created, updated, or deleted.

-   *Action*
    -   *CREATE*

        The log shows the value of the attribute when the resource was created.

    -   *UPDATE*

        The log shows the changed value of the attribute when the resource was updated.

    -   *DELETE*

        The log shows which resource was deleted.


-   *Attribute*

    The attribute of the resource that was created or updated with the relevant operation.

-   *Value*

    The new value of the attribute.

    > ### Note:  
    > There are attributes whose values cannot be displayed in the logs. In such cases the value fields are left blank.


> ### Example:  
> The table shows change logs for the following operations:
> 
> 1.  A tenant administrator, Donna Moore, creates a Company A application.
> 2.  The tenant administrator uploads service provider metadata for the SAML 2.0 trust.
> 3.  The tenant administrator creates custom Company A terms of use by uploading a plain text file.
> 4.  The tenant administrator creates a custom Company A privacy policy by uploading a plain text file.
> 5.  The tenant administrator allows user self-registration for an application of the configured service provider as she uses the default e-mail template for the self-registration process.
> 6.  The tenant administrator configures a branding style for the application.
> 7.  The tenant administrator sets *SAP Community Password Policy v.1.1* for the application .
> 8.  The tenant administrator sets *Company A Terms of Use* for the application.
> 9.  The tenant administrator sets *Company A Privacy Policy* for the application.
> 
> **Sample Change Logs Data**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Date
> 
> 
> 
> </th>
> <th valign="top">
> 
> Administrator's ID
> 
> 
> 
> </th>
> <th valign="top">
> 
> Administrator's Name
> 
> 
> 
> </th>
> <th valign="top">
> 
> Resource Type
> 
> 
> 
> </th>
> <th valign="top">
> 
> Resource ID
> 
> 
> 
> </th>
> <th valign="top">
> 
> Resource Name
> 
> 
> 
> </th>
> <th valign="top">
> 
> Action
> 
> 
> 
> </th>
> <th valign="top">
> 
> Attribute
> 
> 
> 
> </th>
> <th valign="top">
> 
> Value
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:21:21
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> sp.example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Privacy Policy
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A Privacy Policy
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:21:15
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> sp.example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Terms of Use
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A Terms of Use
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:21:08
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> sp.example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Password Policy
> 
> 
> 
> </td>
> <td valign="top">
> 
> https://accounts.sap.com/policy/passwords/sap/web/1.1
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:20:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> sp.example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Branding Style
> 
> 
> 
> </td>
> <td valign="top">
> 
> Text Color=\#ffffff, Background Top Color=\#E3E3E3, Border Color=\#7B9EB3, show\_header=false, Background Bottom Color=\#E3E3E3
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:15:10
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> sp.example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Branding Type
> 
> 
> 
> </td>
> <td valign="top">
> 
> Custom Theme
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:14:29
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> sp.example.com
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Self-Registration
> 
> 
> 
> </td>
> <td valign="top">
> 
> Allowed
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:06:24
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Privacy Policy Document
> 
> 
> 
> </td>
> <td valign="top">
> 
> 53da05f9e4b0732235f24b8e
> 
> 
> 
> </td>
> <td valign="top">
> 
> English Version of Company A Privacy Policy
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Plain Text Privacy Policy File
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:05:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Privacy Policy Document
> 
> 
> 
> </td>
> <td valign="top">
> 
> 53da05f9e4b0732235f24b8a
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A Privacy Policy
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Display Name
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A Privacy Policy
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:03:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Terms of Use Document
> 
> 
> 
> </td>
> <td valign="top">
> 
> 53da0595e4b0732235f24b04
> 
> 
> 
> </td>
> <td valign="top">
> 
> English Version of Company A Terms of Use
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Plain Text Terms of Use File
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 16-05-2014 10:02:21
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Terms of Use Document
> 
> 
> 
> </td>
> <td valign="top">
> 
> 53da0595e4b0732235f24b00
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A Terms of Use
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Display Name
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A Terms of Use
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:32:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> SAML 2.0 Provider Name
> 
> 
> 
> </td>
> <td valign="top">
> 
> company\_a\_service\_provider
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:32:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Authenticating Authority
> 
> 
> 
> </td>
> <td valign="top">
> 
> company\_a\_tenant\_id
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:32:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Assertion Consumer Service Endpoint
> 
> 
> 
> </td>
> <td valign="top">
> 
> service\_provider\_acs\_endpoint, HTTP-POST
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:32:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Single Logout Endpoint
> 
> 
> 
> </td>
> <td valign="top">
> 
> service\_provider\_slo\_endpoint, HTTP-POST
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:32:18
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> UPDATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Single Logout Endpoint
> 
> 
> 
> </td>
> <td valign="top">
> 
> service\_provider\_slo\_endpoint, HTTP-Redirect
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Name ID Attribute
> 
> 
> 
> </td>
> <td valign="top">
> 
> User ID
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Default Name ID Format
> 
> 
> 
> </td>
> <td valign="top">
> 
> urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Self-Registration
> 
> 
> 
> </td>
> <td valign="top">
> 
> Inherit
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Certificate
> 
> 
> 
> </td>
> <td valign="top">
> 
> CN=sp.example.com
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Assertion Consumer Service Endpoint
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Single Logout Endpoint
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> User Attribute
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> 15-05-2014 11:31:11
> 
> 
> 
> </td>
> <td valign="top">
> 
> P123456
> 
> 
> 
> </td>
> <td valign="top">
> 
> Donna Moore
> 
> 
> 
> </td>
> <td valign="top">
> 
> Service Provider
> 
> 
> 
> </td>
> <td valign="top">
> 
> 500964f6e4b0f3cba101f700
> 
> 
> 
> </td>
> <td valign="top">
> 
> Company A \(company\_a\_service\_provider\)
> 
> 
> 
> </td>
> <td valign="top">
> 
> CREATE
> 
> 
> 
> </td>
> <td valign="top">
> 
> Constant Attribute
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> </table>

To download a CSV file with change logs information, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Audit and Change Logs* tile.

3.  Under *Export Change Logs* choose the *Export* button.




<a name="loio9d96aae577f845708b53ebd18dab3745__result_cyl_w4g_qdb"/>

## Results

You have downloaded a CSV file containing history of operations for the tenant administration, and for the configurations of identity providers and service providers.

**Related Information**  


[Troubleshooting for Administrators](../Operation-Guide/troubleshooting-for-administrators-f80beb5.md "This section is intended to help administrators deal with error messages in the administration console for SAP Cloud Identity Services.")

