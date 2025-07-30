<!-- loio4a2d34fd5aa443d7ace316f3b78a6d9d -->

# Call Identity Authentication Certificate Endpoint

The certificate endpoint contains information about the OpenID provider public keys.



The public keys are encoded as JSON Web Key \(JWK\).



<a name="loio4a2d34fd5aa443d7ace316f3b78a6d9d__section_jjd_d4g_lhb"/>

## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/certs</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***GET*



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

`Content-Type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

application/json

</td>
</tr>
<tr>
<td valign="top">

`x-app_tid`

</td>
<td valign="top">

No

</td>
<td valign="top">

Reserved.

</td>
</tr>
<tr>
<td valign="top">

`x-client_id`

</td>
<td valign="top">

No

</td>
<td valign="top">

Reserved.

</td>
</tr>
</table>



### Request Example

```
https://my-tenant.ondemand.com/oauth2/certs
```



<a name="loio4a2d34fd5aa443d7ace316f3b78a6d9d__section_yng_4qg_lhb"/>

## **Response**



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Success

</td>
</tr>
</table>



### Response Payload Example

```

{
  "keys": [{
      "kty": "RSA",
	  "x5t#S256" : "kAQDSY3vl3BuRFLOl-6CaB_VlIWWzcupzYjnWV4BHow",
      "e": "AQAB",
      "use" : "sig",
      "kid" : "VEwv92eXR9jDN9o94GXL8pkWa9Y",
      "x5c" : [ 
"MIIDFjCCAf6gAwIBAQIGAWm+n1AfMA0GCSqGSIb3DQEBBQUAMEoxCzAJBgNVBAYTAkRFMQ8wDQY
DVQQKEwZTQVAtU0UxKjAoBgNVBAMTIXNjaS1kb2N1LmFjY291bnRzNDAwLm9uZGVtYW5kLmNvbTA
eFw0xOTAzMjcxMDA4MjVaFw0yOTAzMjcxMDA4MjVaMEoxCzAJBgNVBAYTAkRFMQ8wDQYDVQQKEwZ
TQVAtU0UxKjAoBgNVBAMTIXNjaS1kb2N1LmFjY291bnRzNDAwLm9uZGVtYW5kLmNvbTCCASIwDQY
JKoZIhvcNAQEBBQADggEPADCCAQoCggEBAKqMOaHOUai+p9wUPO5kARMRkExJfyUwrwHYLCfoGtv
dos74MseRWUdMcMTxlSaVyOSX4eGv9cRW1yQNarounGkTrVhmAkLdhFVcIytdOd1DOKAEvLFGjHX
P5tR0HsFvmGaRQzSS1nTfmW+qvEU6H8GPXnIypx/8wNXBFO52CS3Bx4IioaMSLWY3qJFRHt2paw1
VY/9L8rHGyMAjE458kHjhGXCf1S4iw5Yf79ruIno6PlNx1+QlR90BSy5BheNrDaTqNalnRNmaPt5
55Z4ptSooFumi5Ixw2ngqwtrdCRM6FIWYYLm8/SBzeRWm7N40f3EWbQsLaNyojnBWjIgXGEcCAwE
AAYICAAAwDQYJKoZIhvcNAQEFBQADggEBADNDQvM7ly5LSeYC+a/RfcumB2UnEaw9YZ3o2ymFywW
NstqNsfZ3HTRikAxmtB12wHlKwZLhUaEf3gMAGarPbh+kFbnRHoWOYLQEl+x+Aj7krdul58LnACX
wwTnGeRoZ5M/LlWqTZPDc+lNCIuubwU3F/LIUvXRZOLu/5T3ltjVV3yZ0bM/yxCvXxmX9pv2BmeH
vUYmH9bP7mJcGhbp/puUe9f5YmAur4GbveVDZaL4N2+4qC++dRad1kGzOqIhwXIHzNKt81Hwgll3
DuQcuKvM+I+I9nGXzwpTHB06HmVBNgSofS26bUzi20rD6StOdOIAPFmiimy/r1D6Nmw/Mk50=" ],
      "n": "jjNiLjC91AWhAhsTWxCZ5DmljUioVNzrvtYwpm5nZL3rYVUXfIFGrE5mmAM6zzkcEP9ioPSYsFoPll8_R3akYYi2iKbwEaEoOcSly-
ddL0LGkDIN8A5DDAhpnR49anElaJV87JzuxqpeazY30kw91Wrcohc22rs4vFUXhm4ZCrzK6nmfwTmHStyZb5QiQUGgRMjzbGJ_nOIBdsiMFAZf5BUMkFHjNb45YAlnZrstS2Is-
M6YA_79YntqbPlY2fRZOfEtj5evy6gaj8aCQANzI51Dh6aW3ZpRXphLbYZCLdod05ROTgw-adR_7jKdQCoxNg71qIR_Fka4O8_lugpQ"
  }]
}
 
```



**Related Information**  


[JSON Web Key \(JWK\)](https://tools.ietf.org/html/draft-ietf-jose-json-web-key-41)

