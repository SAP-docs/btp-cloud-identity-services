<!-- loiocea87780bee94c6994b8005c6d6a4815 -->

# Create User Resource \(Deprecated\)

The create user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user.



> ### Note:  
> This API is deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



> ### Note:  
> Create user resource is implemented as defined by the SCIM protocol.



## Request

**URI:**`https://`<Cloud Identity Services domain\>`/service/scim/Users`

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

**HTTP Method:***POST*

**Content-Type: application/scim+json**

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

**Supported Attributes**

-   `emails.value`

    > ### Note:  
    > Only one value is supported.
    > 
    > Values that are part of the respective exclude list can't be used. For more information, see [Restrict User Attributes Values via Exclude Lists](../Operation-Guide/restrict-user-attributes-values-via-exclude-lists-cb108c2.md).
    > 
    > The `<username>` part of the email address can have the following:
    > 
    > -   uppercase and lowercase Latin letters
    > 
    > -   digits from 0 to 9
    > 
    > -   special characters !\#$%&'\*+-/=?^\_\`\{|\}~
    > 
    > -   `.` - cannot be first or last character, or two or more consecutively, unless surrounded by quotation marks.
    > 
    > -   space and the "\(\),:;<\>@\[\\\] characters can be used only if surrounded by quotation marks. The \\ or " must be preceded by \\
    > 
    > 
    > If email is set to not required, `emails.value` can be left empty.
    > 
    > If email is set to not unique, you can create multiple users with the same email.

    > ### Tip:  
    > If email is mandatory, for users without valid email addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or nonexisting domains.

-   `sendMail`

    > ### Note:  
    > The parameter supports Boolean values *true* and *false* in String format. The default value is *true*. If you don’t want to send an email, the value should be passed with value *false*.

-   `mailVerified`

    > ### Note:  
    > The parameter supports Boolean values *true* and *false* in String format. The default value is *false*.

    **Possible Combinations**


    <table>
    <tr>
    <th valign="top">

    Parameter/Result
    
    </th>
    <th valign="top">

    Status/Value
    
    </th>
    <th valign="top">

    Status/Value
    
    </th>
    <th valign="top">

    Status/Value
    
    </th>
    <th valign="top">

    Status/Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `sendMail` 
    
    </td>
    <td valign="top">
    
    *true*
    
    </td>
    <td valign="top">
    
    *true*
    
    </td>
    <td valign="top">
    
    *false*
    
    </td>
    <td valign="top">
    
    *false*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `mailVerified` 
    
    </td>
    <td valign="top">
    
    *true*
    
    </td>
    <td valign="top">
    
    *false*
    
    </td>
    <td valign="top">
    
    *true*
    
    </td>
    <td valign="top">
    
    *false*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Result** 
    
    </td>
    <td valign="top">
    
    The user will receive email. He or she will be able to log on.
    
    </td>
    <td valign="top">
    
    The user will receive email. He or she has to click the verification link in the email.
    
    </td>
    <td valign="top">
    
    The user will be able to log on to the application directly.
    
    </td>
    <td valign="top">
    
    The user will not be able to log on.
    
    </td>
    </tr>
    </table>
    
-   `targetUrl`

    > ### Note:  
    > The URL to the application page that the user should be redirected to after he or she has completed account activation.
    > 
    > If `targetUrl` is not provided, the user is redirected to the Profile Page.
    > 
    > If `targetUrl` is provided, but `sendMail` = `false`, the `targetUrl` value is ignored.

    > ### Remember:  
    > You must add the URL to the list of the trusted domains in the administration console. For more information, see [Configure Trusted Domains](../Operation-Guide/configure-trusted-domains-08fa1fe.md).

-   `name.honorificPrefix`

-   `name.givenName`

    > ### Note:  
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `name.familyName`

    > ### Note:  
    > This attribute is mandatory.
    > 
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `name.middleName`

    > ### Note:  
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `userName`


-   `addresses[work].streetAddress`

-   `addresses[work].locality`

    > ### Note:  
    > The attribute equals to *city*.

-   `addresses[work].region`

    > ### Note:  
    > The attribute is relevant only for Canada and the United States of America. It equals to the *state* in these countries.

-   `addresses[work].postalCode`

-   `addresses[work].country`

-   `addresses[home].streetAddress`

-   `addresses[home].locality`

    > ### Note:  
    > The attribute equals to city.

-   `addresses[home].region`

    > ### Note:  
    > The attribute is relevant only for Canada and the United States of America. It equals to the *state* in these countries.

-   `addresses[home].postalCode`

-   `addresses[home].country`

-   `locale`

    > ### Note:  
    > Must be a string value specified by a two or four-letter code in one of the following formats: XX. Otherwise, the activation email is in English.

-   `password`

    > ### Note:  
    > If the attribute `password` is provided, user is prompted to change the password on first logon. `passwordStatus` will be *initial* as a default value.

-   `passwordStatus`

    > ### Note:  
    > Supported values: `importedPassword`, `initial`, `enabled`, and `disabled`.
    > 
    > If the attribute `password` is provided, user is prompted to change the password on first logon. `passwordStatus` will be *initial* as a default value.

-   `phoneNumbers[work].value`

-   `phoneNumbers[mobile].value`

-   `phoneNumbers[fax].value`

-   `timeZone`

    > ### Note:  
    > The `timeZone` attribute supports the industry-standard Olson time zone \(also known as TZ\) database. For more information, see [Additional Attributes Supported Values](scim-rest-api-deprecated-2f21568.md#loio2f215687fcf34170b0bbc8b36b60f2e9__additional_supported_values).

-   `active`

    > ### Note:  
    > The parameter supports only Boolean values *true* and *false* in Boolean format. They are equivalent to the *active* and *inactive* status in Identity Authentication.
    > 
    > If the *active* parameter is not present in the request the user is created with a status *new*.

-   `displayName`

    > ### Note:  
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `contactPreferenceEmail`

-   `contactPreferenceTelephone`

-   `industryCrm`

-   `company`

-   `companyRelationship`

-   `department`

-   `corporateGroups`

    > ### Note:  
    > This attribute is applicable for the corporate user store scenarios and contains the groups the user in the corporate user store is assigned to.

-   `sourceSystem`
-   `userType`

    > ### Note:  
    > Supported values: *public*, *partner*, *customer*, and *employee*.

-   `telephoneVerified`

    > ### Note:  
    > Supported values: `true` or `false`.

-   `telephoneVerificationAttempts`

    > ### Note:  
    > `telephoneVerificationAttempts` can take values from 0 to 5 including.

-   `passwordPolicy`

    > ### Caution:  
    > We recommend you not to set `passwordPolicy` via the API. If you decide to set `passwordPolicy` via the API make sure the password of the user complies with the password policy you want to set.

    > ### Note:  
    > Sets password policy for the user.
    > 
    > The user is created with no password policy assigned. When the user logs on to an application, he or she takes the password policy of the application. To set a password policy at user creation, use the `passwordPolicy` attribute. Supported values is the URL of the password policy.
    > 
    > -   for *Standard Password Policy* the URL is: `https://accounts.sap.com/policy/passwords/sap/web/1.1` 
    > -   for *Enterprise Password Policy* the URL is: https://accounts.sap.com/policy/passwords/sap/enterprise/1.0
    > -   for *Custom Password Policy* the URL must be taken from a user who has already logged on to an application requiring that custom password policy. To receive the user information, you must execute a *GET* request for the user. The response returns the URL of the password policy that must be used as a value for the request. For more information about the *GET* request, see [User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md).
    > 
    > For more information, about the password policies, see [Configuring Password Policies](../Operation-Guide/configuring-password-policies-12b3395.md).

-   `passwordFailedLoginAttempts`

    > ### Note:  
    > `passwordFailedLoginAttempts` can take values from 0 to 5 including.

-   `otpFailedLoginAttempts`

    > ### Note:  
    > `otpFailedLoginAttempts` can take values from 0 to 4 including.

-   `newsletters`

    > ### Note:  
    > A set of strings.

-   `termsOfUse`
    -   `timeOfAcceptance`

        > ### Note:  
        > `timeOfAcceptance` should be in the format yyyy-MM-dd'T'HH:mm:ss'Z'.

    -   `name`
    -   `id`
    -   `locale`
    -   `version`

-   `privacyPolicy`
    -   `timeOfAcceptance`
    -   `name`
    -   `id`
    -   `locale`
    -   `version`

-   emailTemplateSetId

    > ### Note:  
    > The ID of the email template set. It can be copied from the URL when the email template set is selected in the administration console.
    > 
    > When provided, the newly created user receives on-behalf registration email from the template set whose id is provided.

-   applicationId

    > ### Note:  
    > The ID of the application. It can be copied from the URL when the application is selected in the administration console.
    > 
    > When provided, the newly created user is registered for the application whose ID is provided. The user receives an on-behalf registration email. The account activation page is custom branded for the application. If `home URL` is configured, the user is redirected to it after the account activation. If `targetURL` is provided, the user is redirected to it after the account activation, no matter if the home URL is configured or not.


**Enterprise User Schema Extension**

> ### Note:  
> The values of the following attributes are returned when the Enterprise User Schema Extension is used.

-   `employeeNumber`

-   `costCenter`

-   `organization`

    > ### Note:  
    > Equals the `company` attribute.

-   `division`

-   `department`

    > ### Note:  
    > Equals the `department` attribute from the Core schema.

-   `manager`

    -   `value`

        > ### Note:  
        > The `id` of the user's manager.

    -   `$ref`

        > ### Note:  
        > The resource URL of the manager.

    -   `displayName`

        > ### Note:  
        > Read only.



**Custom Attributes Schema Extension**

Administrators at Identity Authentication can store, read, create and, update customer specific data in up to 10 custom attributes via the SCIM API.

> ### Note:  
> The values of the following attributes are returned when the Custom Attributes Schema Extension \(urn:sap:cloud:scim:schemas:extension:custom:2.0:User\) is used.

-   `attributes`

    -   `name`

        > ### Note:  
        > `name` can take values from `customAttribute1` to `customAttribute10`.

    -   `value`

        > ### Note:  
        > `value` must be in a String format with a maximum length of 256 characters.





## Create User Scenarios

The following scenarios are possible via the SCIM REST API:

**Create New User**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Status/Value

</th>
</tr>
<tr>
<td valign="top">

`password`

</td>
<td valign="top">

provided

</td>
</tr>
<tr>
<td valign="top">

`passwordStatus`

</td>
<td valign="top">

*enabled*

</td>
</tr>
<tr>
<td valign="top">

`sendMail`

</td>
<td valign="top">

*true*

</td>
</tr>
<tr>
<td valign="top">

`mailVerified`

</td>
<td valign="top">

*false*

</td>
</tr>
</table>

**Result**: A new user will be created.

**Create Provisioned User**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Status/Value

</th>
</tr>
<tr>
<td valign="top">

`password`

</td>
<td valign="top">

provided

</td>
</tr>
<tr>
<td valign="top">

`passwordStatus`

</td>
<td valign="top">

*enabled*

</td>
</tr>
<tr>
<td valign="top">

`sendMail`

</td>
<td valign="top">

*true*

</td>
</tr>
<tr>
<td valign="top">

`mailVerified`

</td>
<td valign="top">

*true*

</td>
</tr>
</table>

**Result**: Create a user that is provisioned from another system. The user will be able to log on. He or she will receive email, but does not have to click a verification link in the email.

**Create Corporate User Store User**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Status/Value

</th>
</tr>
<tr>
<td valign="top">

`password`

</td>
<td valign="top">

not provided

</td>
</tr>
<tr>
<td valign="top">

`passwordStatus`

</td>
<td valign="top">

not provided

</td>
</tr>
<tr>
<td valign="top">

`sendMail`

</td>
<td valign="top">

*false*

</td>
</tr>
<tr>
<td valign="top">

`mailVerified`

</td>
<td valign="top">

*true*

</td>
</tr>
</table>

**Result**: Create a user that comes from the corporate user store. The user will be able to log on to the application directly.



## Request Example



## Example

```json


{
    
    "userName": "johnsmith",

    "name": {

        "givenName": "John",

        "familyName": "Smith",
        
        "middleName": "Smith",

        "honorificPrefix": "Mr."

    },

    "emails": [{

        "value": "john.smith@sap.com"

    }],

    "addresses": [{

        "type": "work",

        "streetAddress": "100 Universal City Plaza",

        "locality": "Hollywood",

        "region": "CA",

        "postalCode": "91608",

        "country": "US"

    }, {

        "type": "home",

        "streetAddress": "456 Hollywood Blvd",

        "locality": "Hollywood",

        "region": "CA",

        "postalCode": "91608",

        "country": "US"

    }],

    "phoneNumbers": [{

        "value": "555-555-5555",

        "type": "work"

    }, {

        "value": "555-555-4444",

        "type": "mobile"

    }, {

        "value": "555-555-4444",

        "type": "fax"

    }],

    "locale": "DE",

    "timeZone": "Europe/Berlin",
	
	"displayName": "johnsmith",

    "contactPreferenceEmail": "yes",

    "contactPreferenceTelephone": "no",

    "industryCrm": "Consumer Products",

    "companyRelationship": "Partner",

    "company": "SFSF",

    "department": "Administration",

    "password": "Abcd1234",

    "userType": "partner",

    "active": true,

    "passwordStatus": "enabled",

    "sendMail":"false",
     
    "mailVerified": "true", 

    "telephoneVerified": "true",  

    "termsOfUse":  [{

		"timeOfAcceptance": "2015-08-21T11:19:50Z",

        "name": "ToU",

        "id": "ToU",

        "locale": "en_US",

        "version": "1" 
		}
	  ],

    "privacyPolicy": [{
		 
		"timeOfAcceptance": "2015-08-21T11:19:50Z",

        "name": "PP",
                         
        "id": "b3452casd-8670-7341-945h-5e0288b9gee4", 

        "locale": "en_US",

        "version": "1" 
       }
     ],
     
    "corporateGroups": [
    {
        "value": "admin"
    }
  ], 

    "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User" : {

        "employeeNumber" : "JohnS",
 
        "costCenter" : "costCenter",

        "organization" : "SFSF",

        "division" : "Finance",

        "department" : "Administration",

        "manager" : {

          "value" : "P999913",

          "$ref" : "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P999913"

       }
     },

    "urn:sap:cloud:scim:schemas:extension:custom:2.0:User":{ 
        
       "attributes":[{ 

         "name":"customAttribute1",

         "value":"Home Address2"

         },

         { 

         "name":"customAttribute2",

         "value":"Telephone2"

         }

    ]}
    
}

```



## Response

**Format**: *application/scim+json*

**Response Status Codes**

**Success or Error Codes**


<table>
<tr>
<th valign="top">

Response Code

</th>
<th valign="top">

Meaning

</th>
<th valign="top">

Response Description

</th>
</tr>
<tr>
<td valign="top">

201

</td>
<td valign="top">

Created

</td>
<td valign="top">

Indicates success

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Bad Request

</td>
<td valign="top">

-   If user with `id` provided in the `value` attribute of the `manager` attribute from the enterprise schema does not exist.

-   If `applicationId` is not valid.

-   If the template set for the `emailTemplateSetId` doesn't contain on-behalf registration email.



</td>
</tr>
</table>

The URI of the newly created user is in the location header of the HTTP Response.



## Response Example



## Example

```json

Location: https://<tenant ID>.accounts.ondemand.com/service/users/P057607

 

 

Body:

 

{

"schemas": [

        "urn:ietf:params:scim:schemas:core:2.0:User", "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",

        "urn:sap:cloud:scim:schemas:extension:custom:2.0:User"],

    "userName": "johnsmith",

    "id": "P057607",

    "userUuid": "5ac8c345-5da4-4530-8g14-1234h26373yz",			

    "meta": {

        "location": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000000",

        "resourceType": "User",

        "version": "1.0",

        "created": "2013-06-18T13:05:51Z",

        "lastModified": "2015-08-21T11:19:50Z"

    },

    "name": {

        "givenName": "John",

        "familyName": "Smith",

		"middleName": "Smith",

        "honorificPrefix": "Mr."

    },

    "emails": [{

        "value": "john.smith@sap.com"

    }],

    "addresses": [{

        "type": "work",

        "streetAddress": "100 Universal City Plaza",

        "locality": "Hollywood",

        "region": "CA",

        "postalCode": "91608",

        "country": "US"

    }, {

        "type": "home",

        "streetAddress": "456 Hollywood Blvd",

        "locality": "Hollywood",

        "region": "CA",

        "postalCode": "91608",

        "country": "US"

    }],

    "phoneNumbers": [{

        "value": "555-555-5555",

        "type": "work"

    }, {

        "value": "555-555-4444",

        "type": "mobile"

    }, {

        "value": "555-555-4444",

        "type": "fax"

    }],

    "locale": "DE",

    "timeZone": "Europe/Berlin",

    "userType": "partner",

	"mailVerified": "true";

    "active": true,
    
    }],

    "displayName": "John Smith",

    "contactPreferenceEmail": "yes",

    "contactPreferenceTelephone": "no",

    "industryCrm": "Consumer Products",

    "company": "SFSF",

    "department": "Administration",
       
    "telephoneVerified": "true",

    "termsOfUse":  [{

		"timeOfAcceptance": "2015-08-21T11:19:50Z",

        "name": "ToU",

        "id": "ToU",

        "locale": "en_US",

        "version": "1" 
		}
	  ],

     "privacyPolicy": [{
		 
		"timeOfAcceptance": "2015-08-21T11:19:50Z",

        "name": "PP",
                         
        "id": "b3452casd-8670-7341-945h-5e0288b9gee4", 

        "locale": "en_US",

        "version": "1" 
       }
     ],
       
    "corporateGroups": [
    {
      "value": "admin"
    }
  ], 

    "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User" : {

       "employeeNumber" : "JohnS",

       "costCenter" : "costCenter",

       "organization" : "SFSF",

       "division" : "Finance",

       "department" : "Administration",

       "manager" : {

         "value" : "P999913",

         "$ref" : "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P999913",

         "displayName" : "Jane Watson"

         }

       },

    "urn:sap:cloud:scim:schemas:extension:custom:2.0:User" : {

      "attributes" : [ {

        "name" : "customAttribute1",

        "value" : "Home Address2"

      }, {

        "name" : "customAttribute2",

        "value" : "Telephone2"

      } ]

    }

}
```

**Related Information**  


[Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md "The user search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for user search. User search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol for querying and filtering resources.")

[User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md "The user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known user.")

[Update User Resource \(Deprecated\)](update-user-resource-deprecated-9e36479.md "The update user method of the implementation of the SCIM REST API protocol provides information on the update of a known user. The method does not create a new user.")

[Delete User Resource \(Deprecated\)](delete-user-resource-deprecated-436015d.md "The delete user resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing user. Delete user resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

