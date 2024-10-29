<!-- loioe957782821024ee3bc32251ff7baa21e -->

# Handling Specific Attributes

Manage specific user and group attributes during the provisioning of entities to different systems.



<a name="loioe957782821024ee3bc32251ff7baa21e__section_zms_ywj_pcc"/>

## SAP HANA Database Username and Email

In SAP HANA Cloud, SAP HANA Database, users have an immutable HANA database username and are not expected to have an associated email. This affects provisioning scenarios, particularly with Identity Authentication, and requires changes in the transformations.

When users are provisioned from Identity Authentication to SAP HANA Cloud, SAP HANA Database, the **userID** attribute \(P-user in Identity Authentication\) is mapped to the **userId** attribute \(HANA database username in SAP HANA Cloud, SAP HANA Database\) and provisioned accordingly. The HANA database username should not to be confused with UserName. Given that the User ID in Identity Authentication is unique only within a specific tenant, consider the following cases when your organization uses multiple tenants:



### Use Case 1 - Change tenants

-   You have two SAP Cloud Identity Services tenants \(tenant 1 and tenant 2\).

-   You have provisioned the users from tenant 1 to SAP HANA Cloud, SAP HANA Database.

-   Now you want to change tenant 1 with tenant 2 and start provisioning the users from tenant 2 to SAP HANA Cloud, SAP HANA Database.


In this case, one and the same user in tenant 1 and tenant 2 might have different P user values. For example: John Smith \(P000001\) exists in tenant 1 and John Smith \(P000002\) exists in tenant 2. The Identity Provisioning won’t be able to transfer the value from tenant 2, because the HANA database username is immutable.

We suggest handling this as follows:

1.  Delete the affected users in the target SAP HANA Cloud, SAP HANA Database system. That is, John Smith \(P000001\).

2.  Run a provisioning job from the Identity Authentication source system in your tenant 2.

    As a result, the user John Smith will be provisioned with his P000002 P user.




### Use Case 2 - Use more than one tenant

-   You have two SAP Cloud Identity Services tenants \(tenant 1 and tenant 2\) in different regions, for example, and you want to use both.


In this case, different users in tenant 1 and tenant 2 might have the same P user value. For example, John Smith \(P000001\) in tenant 1 \(Europe\) and Julie Armstrong \(P000001\) in tenant 2 \(Asia\).

We suggest handling this as follows:

1.  Modify the read transformation in the Identity Authentication source system of your tenant 1 by adding, for example, a prefix or a suffix to the P user value.


    <table>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "functions": [
    >     {
    >       "function": "concatString",
    >       "prefix": "Europe_"
    >     }
    >   ]
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "functions": [
    >     {
    >       "function": "concatString",
    >       "suffix": "_Europe"
    >     }
    >   ]
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
2.  Modify the read transformation in the Identity Authentication source system of your tenant 2 by adding, for example, a prefix or a suffix to the P user value.


    <table>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "functions": [
    >     {
    >       "function": "concatString",
    >       "prefix": "Asia_",
    >     }
    >   ]
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >   "functions": [
    >     {
    >       "function": "concatString",
    >       "suffix": "_Asia"
    >     }
    >   ]
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
3.  Run provisioning jobs from both Identity Authentication source systems in tenant 1 and tenant 2.

    As a result, you will distinguish the different users with the same P user value by adding a prefix.




### Use Case 3 - Email of SAP HANA Database User

-   You want to provision SAP HANA Database users to Identity Authentication. The users don't have email addresses, as this is neither expected nor needed. However, email is a required user attribute in Identity Authentication.


We suggest handling this as follows:

1.  Modify the read transformation in the SAP HANA Cloud, SAP HANA Database source system to construct a fictitious email address by appending the username with a suffix that includes the "@" sign and a domain.

    > ### Code Syntax:  
    > ```
    > {
    >   "sourcePath": "$.userName",
    >   "targetPath": "$.emails[0].value",
    >   "functions": [
    >     {
    >       "function": "concatString",
    >       "suffix": "@test.test"
    >     }
    >   ]
    > }
    > ```

2.  Run a provisioning job from the source system.

    As a result, you will meet the following condition of the target Identity Authentication: `"condition": "($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)",` and the job will not fail due to a missing required attribute.


**Related Information**  


[Administration Issues](administration-issues-90ce2d5.md "")

[Job and Transformation Issues](job-and-transformation-issues-dbe3c08.md "")

[Error Messages](error-messages-ad525a4.md "")

[Additional Information](additional-information-7463572.md "")

