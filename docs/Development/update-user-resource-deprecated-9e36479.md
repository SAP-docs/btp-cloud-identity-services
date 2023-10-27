<!-- loio9e36479e92ca4b0db75f085d4ab3aa23 -->

# Update User Resource \(Deprecated\)

The update user method of the implementation of the SCIM REST API protocol provides information on the update of a known user. The method does not create a new user.



> ### Note:  
> This API is deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



> ### Note:  



## Request

**URI:**`Update is provided only on the attributes with new values. The other attributes remain the https://<tenant ID>.accounts.ondemand.com/service/scim/Users/<id>`

**HTTP Method:***PUT*

**Content-Type: application/scim+json**

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

**Supported Attributes**

Attributes are case-sensitive and only the exact case must be used.

-   id

    > ### Note:  
    > Attribute `id` is required in the request json and must match the path parameter `id`.

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

    > ### Tip:  
    > If email is mandatory, for users without valid email addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or nonexisting domains.

-   `name.honorificPrefix`

-   `name.givenName`

    > ### Note:  
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `name.familyName`

    > ### Note:  
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `name.middleName`

-   `userName`


-   `addresses[work].streetAddress`

-   `addresses[work].locality`

    > ### Note:  
    > The attribute equals to city.

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

-   `phoneNumbers[work].value`

-   `phoneNumbers[mobile].value`

-   `phoneNumbers[fax].value`

-   `timeZone`

-   `active`

    > ### Note:  
    > If the `active` parameter and its value are not present in the request, the user status remains unchanged.

-   `displayName`

    > ### Note:  
    > The characters `<`, `>`, `:` are not allowed for this attribute.

-   `contactPreferenceEmail`

-   `contactPreferenceTelephone`

-   `industryCrm`

-   `company`

-   `companyRelationship`

    > ### Note:  
    > If the `userType` attribute is provided and has one of the values `Customer`, `Employee`, or `Partner`, the `companyRelationship` attribute value is overwritten and takes the same value as the `userType` attribute.

-   `department`

-   `corporateGroups`

    > ### Note:  
    > This attribute is applicable for the corporate user store scenarios and contains the groups the user in the corporate user store is assigned to. The following options are possible:
    > 
    > -   If the attribute corporateGroups is provided with a specific value, this value overwrites the previous one.
    > -   If the attribute corporateGroups is not provided, this previous value of the attribute is preserved.
    > -   If the attribute corporateGroups is provided without a value, the previous value is deleted.

-   `password`

    > ### Note:  
    > If attribute `password` is provided the password will be changed.

    > ### Tip:  
    > [Configure SAML 2.0 Service Provider](../Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md).

-   `passwordStatus`

    > ### Note:  
    > If the `password` attribute is provided the `passwordStatus` can be set to `enabled` or `initial`. When this attribute is provided the `password` attribute is a required parameter.

    > ### Tip:  
    > [Configure SAML 2.0 Service Provider](../Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md).

-   `userType` 

    > ### Note:  
    > Supported values: `public`, `partner`, `customer`, and `employee`.

-   `mailVerified`

    > ### Note:  
    > The parameter supports Boolean values *true* and `false` in String format. The default value is *false*.

-   `telephoneVerified`

    > ### Note:  
    > Supported values: `true` or `false`.

-   `telephoneVerificationAttempts`

    > ### Note:  
    > `telephoneVerificationAttempts` can take values from 0 to 5 including.

-   `passwordPolicy`

    > ### Caution:  
    > We recommend you not to update `passwordPolicy` via the API. If you decide to set via the API make sure the password of the user complies with the password policy,`passwordPolicy` you want to set.

    > ### Note:  
    > Updates the password policy for the user. Supported values is the URL of the password policy.
    > 
    > -   for *Standard Password Policy* the URL is: `https://accounts.sap.com/policy/passwords/sap/web/1.1` 
    > -   for *Enterprise Password Policy* the URL is: https://accounts.sap.com/policy/passwords/sap/enterprise/1.0
    > -   for *Custom Password Policy* the URL must be taken from a user who has already logged on to an application requiring that custom password policy. To receive the user information, you must execute a *GET* request for the user. The response returns the URL of the password policy that must be used as a value for the request. For more information about the *GET* request, see [User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md).
    > 
    > For more information, about the password policies, see [Configuring Password Policies](../Operation-Guide/configuring-password-policies-12b3395.md).

-   `passwordStatus`

    > ### Note:  
    > Supported values: `importedPassword`, `initial`, `enabled`, and `disabled`.

-   `passwordFailedLoginAttempts`

    > ### Note:  
    > `passwordFailedLoginAttempts` can take values from 0 to 5 including.

-   `otpFailedLoginAttempts`

    > ### Note:  
    > `otpFailedLoginAttempts` can take values from 0 to 4 including.

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

        > ### Note:  
        > `timeOfAcceptance` must be in the format yyyy-MM-dd'T'HH:mm:ss'Z'.

    -   `name`
    -   `id`
    -   `locale`
    -   `version`


**Enterprise User Schema Extension**

> ### Note:  
> The values of the following attributes are returned when the Enterprise User Schema Extension is used.

-   `employeeNumber`

-   `costCenter`

-   `organization`

    > ### Note:  
    > Equals the `company` attribute from the Core schema.

-   `division`

-   `department`

    > ### Note:  
    > Equals the `department` attribute from the Core schema.

-   `manager`

    -   `value`

    -   `$ref`

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
        > `value` must be string with a maximum length of 256 characters.
        > 
        > If you provide empty `value`, it will delete the attribute if it already exists.
        > 
        > If you provide an empty list of `attributes`, the custom attributes that are already set will be deleted.





## Request Example



## Example

```json

{

    "userName": "johnsmith",

    "id": "P000000",

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

    "active": true,
    
    }],

    "displayName": "John Smith",

    "contactPreferenceEmail": "yes",

    "contactPreferenceTelephone": "no",

    "industryCrm": "Consumer Products",

    "companyRelationship": "Partner",

    "company": "SFSF",

    "department": "Administration",

    "password": "Abcd1234",
  	
    "passwordStatus": "enabled", 
 
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

200

</td>
<td valign="top">

OK

</td>
<td valign="top">

Operation successful

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

If user with `id` provided in the `value` attribute of the `manager` attribute from the enterprise schema does not exist.

</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [Error and Success Codes](error-and-success-codes-7f87a75.md).



## Response Example



## Example

```json

{

"schemas": [

        "urn:ietf:params:scim:schemas:core:2.0:User", "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",

        "urn:sap:cloud:scim:schemas:extension:custom:2.0:User"],
   
    "userName": "johnsmith",

    "meta": {

        "location": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000000",

        "resourceType": "User",

        "version": "1.0",

        "created": "2013-06-18T13:05:51Z",

        "lastModified": "2015-08-21T11:19:50Z"

    },

    "id": "P000000",

    "userUuid": "5ac8c345-5da4-4530-8g14-1234h26373yz",

    "name": {

        "givenName": "John",

        "familyName": "Smith",

		"middleName": "Smith",

        "honorificPrefix": "Mr."

    },

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

    "active": true,
  
    }],

    "displayName": "John Smith",

    "contactPreferenceEmail": "yes",

    "contactPreferenceTelephone": "no",

    "industryCrm": "Consumer Products",

    "companyRelationship": "Partner",

    "company": "SFSF",

    "department": "Administration",

    "passwordStatus" : "enabled",
     
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

         "$ref" : "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P999913",

         "displayName" : "Jane Watson"

     }

        },

     "urn:sap:cloud:scim:schemas:extension:custom:2.0:User":

     {

        "attributes":

        [

           {

           "name": "customAttribute1",

           "value": "Home Address2"

           },

           {

           "name": "customAttribute2",

           "value": "Telephone2"

          }

       ]

    }

}
```

**Related Information**  


[Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md "The user search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for user search. User search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol for querying and filtering resources.")

[User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md "The user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known user.")

[Create User Resource \(Deprecated\)](create-user-resource-deprecated-cea8778.md "The create user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user.")

[Delete User Resource \(Deprecated\)](delete-user-resource-deprecated-436015d.md "The delete user resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing user. Delete user resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

