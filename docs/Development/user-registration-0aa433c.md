<!-- loio0aa433c741a24df9ac2b3a5faca202de -->

# User Registration

The user registration is used for registration of new users or for on-behalf registration of partners.



<a name="loio0aa433c741a24df9ac2b3a5faca202de__section_mbm_1xk_fdb"/>

## Prerequisites

You need to set up the authentication type to access the API. For more information about this configuration, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



<a name="loio0aa433c741a24df9ac2b3a5faca202de__section_vc3_rlj_fdb"/>

## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/users`

**HTTP Method:***POST*



### Request Headers


<table>
<tr>
<th valign="top">

Header



</th>
<th valign="top">

Required



</th>
<th valign="top">

Values



</th>
</tr>
<tr>
<td valign="top">

`Basic Authorization`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

For more information, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



</td>
</tr>
<tr>
<td valign="top">

`Content-Type`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

application/x-www-form-urlencoded



</td>
</tr>
</table>



### Request Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Required



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
<th valign="top">

Parameter Type



</th>
</tr>
<tr>
<td valign="top">

`email`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

The e-mail of the user you register. The e-mail must be unique.

> ### Tip:  
> If e-mail is mandatory, for users without valid e-mail addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or non-existing domains.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`user_profile_id`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The user ID



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`login_name`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The logon name of the user



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`first_name`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The first name of the user you register. The allowed maximum length for the first name is 32 characters.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`last_name`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

The last name of the user you register. The allowed maximum length for the last name is 64 characters.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`language`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The preferred language for the activation e-mail of the user you register. The usage of this parameter does not affect the end-user screens.

Must be a string value specified by a two or four-letter code in one of the following formats: XX, xx, xx-XX or xx\_XX. Otherwise the activation e-mail is in English.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`valid_from`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The *valid from* date



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`valid_to`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The *valid until* date



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`name_id`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The name ID of the user you register.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`source_url`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The URL to the public page of the application where the Identity Authentication overlays are integrated. If not provided, the activation screen is shown without overlays. This parameter value must be URL-encoded.

> ### Caution:  
> Put **`/`** at the end of the source URL.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`target_url`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The URL to the application page that the user should be redirected to after he or she has completed account activation. If `target_url` is not provided, the user is redirected to the home URL configured for the service provider. For more information how to configure *Home URL*, see [Configure an Application's Home URL](../Operation-Guide/configure-an-application-s-home-url-be6d6f2.md).



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`send_email`



</td>
<td valign="top">

No



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

Values: true \(default value\), false

-   If **true** - activation e-mail is sent to the user.

-   If **false** - activation e-mail is not sent to the user.

    > ### Note:  
    > If the user is new, the link for account activation is returned with the **201** response.




</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute1`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Custom attributes are used to store additional information for the SP users. It is allowed to pass five customer attributes for a user



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute2`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Custom attributes are used to store additional information for the SP users. It is allowed to pass five customer attributes for a user



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute3`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Custom attributes are used to store additional information for the SP users. It is allowed to pass five customer attributes for a user



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute4`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Custom attributes are used to store additional information for the SP users. It is allowed to pass five customer attributes for a user



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

spCustomAttribute5



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Custom attributes are used to store additional information for the SP users. It is allowed to pass five customer attributes for a user



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example



> ### Caution:  
> All parameters for the POST method must be written on one line.

```
POST /service/users
Content-Type: application/x-www-form-urlencoded

name_id=johns&user_profile_id=p987654&email=john.smith@sap.com&first_name=John&last_name=Smith&language=en&valid_from=20110901120000Z&valid_to=20120901110000Z&source_url=http%3A%2F%2Fwww.myapp.com%2Fpublic.jsp&target_url=http%3A%2F%2Fwww.myapp.com%2Fprotected.jsp&spCustomAttribute1=Industry
```





<a name="loio0aa433c741a24df9ac2b3a5faca202de__section_xvr_ylj_fdb"/>

## Response



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Reason



</th>
<th valign="top">

Description



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

The user is successfully created.



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

The user for whom you are trying to create an SP user is `inactive`.



</td>
</tr>
<tr>
<td valign="top">

409



</td>
<td valign="top">

Conflict



</td>
<td valign="top">

The SP user already exists.



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [General Error Codes](general-error-codes-182352d.md).



### Response Example



The URI of the created user is returned in the location header of the HTTP Response.

```
Location: https://<tenant ID>.accounts.ondemand.com/service/users/0800200c9a66
```



In case of conflict, the URI of the conflicting user is returned in the location header of the HTTP Response.

```
Location: https://<tenant ID>.accounts.ondemand.com/service/users/467345637aa
```



In case of creating a new user with "send\_email=false", the activation link is returned in the HTTP Response body.

```

Content-Type: application/json

    {

         "activationLink" : "https://<tenant ID>.accounts.ondemand.com/ids/activation?token=I1830C497BF9B857B7D6298E5F117AF397I1F59A28838A3276E8B68FFFF54414C8843ACF395A05401ABE6568FF3659D6EE96"

    }

```



 

**Related Information**  


[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

