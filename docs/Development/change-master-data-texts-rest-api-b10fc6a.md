<!-- loiob10fc6a9a37c488a82ce7489b1fab64c -->

# Change Master Data Texts REST API

The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.



## Prerequisites

To call the methods of this Change Master Data Texts REST API you must have a system as administrator with an assigned *Manage Tenant Configuration* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).



## Usage

The predefined master data represents records in Identity Authentication that contain all relevant system data about a resource \(Salutations, Functions, Departments, Company Relationships, Industries, Languages, Countries\). That data can be used by the system for different classifications in the organization, for example, job titles, departments, or countries. The predefined master data texts are stored in `properties` documents which can be accessed from the links in the table below.

**Predefined Master Data Texts**


<table>
<tr>
<th valign="top">

Resource



</th>
<th valign="top">

Link



</th>
<th valign="top">

Notes



</th>
</tr>
<tr>
<td valign="top">

Salutations



</td>
<td valign="top">

 [Salutations.properties](change-master-data-texts-rest-api-b10fc6a.md#loiod4512bcbe9c8439896e06425f247c7af) 



</td>
<td valign="top">

Key value pairs with a predefined set of honorifics.



</td>
</tr>
<tr>
<td valign="top">

Functions



</td>
<td valign="top">

 [Functions.properties](change-master-data-texts-rest-api-b10fc6a.md#loio78cb6d43814c4b179eda8282c28e8d2f) 



</td>
<td valign="top">

Key value pairs with a predefined set of job titles.



</td>
</tr>
<tr>
<td valign="top">

Departments



</td>
<td valign="top">

 [Departments.properties](change-master-data-texts-rest-api-b10fc6a.md#loiod13c638f0d5d4a8889debf278fcb0275) 



</td>
<td valign="top">

Key value pairs with a predefined set of departments.



</td>
</tr>
<tr>
<td valign="top">

Company Relationships



</td>
<td valign="top">

 [Relationships.properties](change-master-data-texts-rest-api-b10fc6a.md#loiof7eb5b72aed440fdb75657379bd368d1) 



</td>
<td valign="top">

Key value pairs with a predefined set of business entities, such as customer, partner, employee.



</td>
</tr>
<tr>
<td valign="top">

Industries



</td>
<td valign="top">

 [Industries.properties](change-master-data-texts-rest-api-b10fc6a.md#loioe62f9b8fde264f3ab644bdaa5a7876e2) 



</td>
<td valign="top">

Key value pairs with a predefined set of industries.



</td>
</tr>
<tr>
<td valign="top">

Languages



</td>
<td valign="top">

 [Languages.properties](change-master-data-texts-rest-api-b10fc6a.md#loio3be819bd3a3a498fa287542346a7add0) 



</td>
<td valign="top">

Key value pairs with a predefined set of languages.



</td>
</tr>
<tr>
<td valign="top">

Countries



</td>
<td valign="top">

 [Countries.properties](change-master-data-texts-rest-api-b10fc6a.md#loioe4e7e4c52cf04295bf94465eba7ceaaa) 



</td>
<td valign="top">

Key value pairs with a predefined set of countries.



</td>
</tr>
</table>

The files contain configurable parameters stored as key value pairs of strings. Each key stores the unified key of the resource, and the corresponding value is the unified value of the resource that can be changed and updated.

The example below shows the customized values of the *Functions* file. The dropdown list in the *Job Function* field on the *Registration* form shows the new values that have overwritten the predefined texts in the file.

![](../Operation-Guide/images/Master_Data_Texts_e1d1331.png)

Depending on your requirements, you can:

-   Use the **GET** method to obtain the texts that you have already overwritten in the predefined master data texts, change the texts that you want, add them to the **POST** request and upload them.
-   Use the **GET** method to obtain the texts that you have already overwritten in the predefined master data texts, delete a key value pair, add the texts without this line to the **POST** request and upload them. This will replace the deleted key value pair with the predefined one.
-   Open the respective `properties` document from the link in the table, use the **GET** method to obtain the texts that overwrote part of the predefined master data texts when your custom tenant was created, from the downloaded file copy the key value pairs that were not included in the response, change the texts in the copied key value pairs, add these new key value pairs to the **POST** request, and execute it.
-   Open the respective `properties` document from the link in the table, copy it to the **POST** request, and execute it. This will replace all texts with the predefined ones.

> ### Caution:  
> Be careful if you change the keys when overwriting data texts, because this can result in invalid values. If a user has a certain value assigned, and the key value pair is overwritten with a different key, then the value for that property of the user will be no longer valid and visualized. For example, if you have set "Mr." to a user, and the key-value pair is "01=Mr.". If you overwrite the key value pair with "03=Mr.", "Mr." will not be visualized for that user.
> 
> When overwriting data texts, the keys for the different languages must be one and the same. For example, the master data texts for the German locale are overwritten, and the tenant administrator wants to overwrite the texts for the French locale. The keys for the German locale should be obtained first and used as keys for the French locale. After that the values can be translated in French.



## Methods


<table>
<tr>
<th valign="top">

HTTP Method



</th>
<th valign="top">

See



</th>
<th valign="top">

URI



</th>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[GET Master Data Texts](change-master-data-texts-rest-api-b10fc6a.md#loiob2f411ec61104f178e665498d2550149)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_<VALUE>&locale=<value>`** 



</td>
</tr>
<tr>
<td valign="top">

*POST*



</td>
<td valign="top">

[POST Master Data Texts](change-master-data-texts-rest-api-b10fc6a.md#loio26691a9f2e024f598b976f2268a5efbd)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/resource/SAP_DEFAULT`** 



</td>
</tr>
</table>

> ### Note:  
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*.

**Related Information**  


[Identity Directory SCIM REST API](identity-directory-scim-rest-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password e-mail.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[General Error Codes](general-error-codes-182352d.md "The following table lists error codes that may be returned from any method on any resource URI.")

 <a name="loiob2f411ec61104f178e665498d2550149"/>

<!-- loiob2f411ec61104f178e665498d2550149 -->

## GET Master Data Texts

Download the texts that you have already overwritten in the predefined master data texts.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=<value>&locale=<value>`

**HTTP Method:***GET*

**Permissions:**You must have a system as administrator with an assigned *Manage Tenant Configuration* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).



### URL Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Required



</th>
<th valign="top">

Description



</th>
<th valign="top">

Notes



</th>
</tr>
<tr>
<td valign="top">

`setId`



</td>
<td valign="top">

No



</td>
<td valign="top">

The identifier of the scenario that the resource is related to.



</td>
<td valign="top">

The default value is`SAP_DEFAULT`



</td>
</tr>
<tr>
<td valign="top">

`resourceType`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The type of the resource.



</td>
<td valign="top">

Use:

-   `RESOURCE_MD_SALUTATIONS`
-   `RESOURCE_MD_FUNCTIONS`
-   `RESOURCE_MD_DEPARTMENTS`
-   `RESOURCE_MD_RELATIONSHIPS`
-   `RESOURCE_MD_INDUSTRIES`
-   `RESOURCE_MD_LANGUAGES`
-   `RESOURCE_MD_COUNTRIES`



</td>
</tr>
<tr>
<td valign="top">

`locale`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The locale of the resource.



</td>
<td valign="top">

The default languages are:

-   Chinese \(zh\_CN\)
-   Dutch \(nl\)
-   English \(en\)
-   French \(fr\)
-   German \(de\)
-   Hebrew \(iw\)
-   Italian \(it\)
-   Japanese \(ja\)
-   Korean \(ko\)
-   Polish \(pl\)
-   Portuguese \(pt\)
-   Russian \(ru\)
-   Spanish \(es\)
-   Welsh \(cy\)
-   Swedish \(sv\)



</td>
</tr>
</table>



### Request Example

```
GET /service/resource?resourceType=RESOURCE_MD_SALUTATIONS&locale=en

Content-Type: application/json
```



## Response



### Response Status and Error Codes

**Success Codes**


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

200 OK



</td>
<td valign="top">

The request was successful.



</td>
<td valign="top">

OK



</td>
</tr>
</table>

**Error Codes**


<table>
<tr>
<th valign="top">

Response Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

*400*



</td>
<td valign="top">

Bad Request



</td>
<td valign="top">

Validate JSON data. Validate that the special characters are escaped properly and new lines are added.



</td>
</tr>
<tr>
<td valign="top">

*401*



</td>
<td valign="top">

Unauthorized



</td>
<td valign="top">

The client is not authenticated.



</td>
</tr>
<tr>
<td valign="top">

*403*



</td>
<td valign="top">

Forbidden



</td>
<td valign="top">

Access to the resource is denied.



</td>
</tr>
<tr>
<td valign="top">

*404*



</td>
<td valign="top">

Not Found



</td>
<td valign="top">

The requested resource cannot be found.



</td>
</tr>
<tr>
<td valign="top">

*405*



</td>
<td valign="top">

Method Not Allowed



</td>
<td valign="top">

The requested method is not supported for the given resource.



</td>
</tr>
<tr>
<td valign="top">

*415*



</td>
<td valign="top">

Unsupported Media Type



</td>
<td valign="top">

The REST service does not support the API version requested by the REST client.



</td>
</tr>
<tr>
<td valign="top">

*500*



</td>
<td valign="top">

Internal Server Error



</td>
<td valign="top">

The operation cannot be completed due to a server error.



</td>
</tr>
<tr>
<td valign="top">

*503*



</td>
<td valign="top">

Service Unavailable



</td>
<td valign="top">

The service is currently unavailable.



</td>
</tr>
</table>



### Response Example

Example of response that returns overwritten values of the *Salutations* file.

```
				
{
  0001=Dr.,
  0002=Prof.
}

```

Example of response that returns overwritten keys of the *Salutations* file. The keys can differ from the original in the master data file. It is not necessary to be in sequence.

```
				
{
  01=Ms.,
  05=Mr.
}

```

 <a name="loio26691a9f2e024f598b976f2268a5efbd"/>

<!-- loio26691a9f2e024f598b976f2268a5efbd -->

## POST Master Data Texts

Update the master data texts.



> ### Caution:  
> Make sure that you have applied the proper escaping in your **POST** request.
> 
> You should add *\\n* at the end of each line in the data property content.
> 
> **Escape Sequences**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Value
> 
> 
> 
> </th>
> <th valign="top">
> 
> Escape Sequences
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> \\b
> 
> 
> 
> </td>
> <td valign="top">
> 
> Backspace \(ascii code 08\)
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> \\f
> 
> 
> 
> </td>
> <td valign="top">
> 
> Form feed \(ascii code 0C\)
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> \\n
> 
> 
> 
> </td>
> <td valign="top">
> 
> New line
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> \\r
> 
> 
> 
> </td>
> <td valign="top">
> 
> Carriage return
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> \\t
> 
> 
> 
> </td>
> <td valign="top">
> 
> Tab
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> \\"
> 
> 
> 
> </td>
> <td valign="top">
> 
> Double quote
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> \\\\
> 
> 
> 
> </td>
> <td valign="top">
> 
> Backslash character
> 
> 
> 
> </td>
> </tr>
> </table>

> ### Tip:  
> Instead of editing the request manually, you can use an on-line tool for converting a normal string into a quoted one.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/resource/SAP_DEFAULT`

**HTTP Method:****POST**

**Permissions:**You must have a system as administrator with an assigned *Manage Tenant Configuration* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).



### Request Example

```
https://<tenantId>.accounts.ondemand.com/service/resource/SAP_DEFAULT
Content-Type: application/json

Body:

[{

"resourceType": "RESOURCE_MD_DEPARTMENTS",

"locale": "en",

"contentType": "text/html;charset=UTF-8",

"data": "01=HR\n02=IT"
}]

```



## Response



### Response Status and Error Codes

**Success Codes**


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

200 OK



</td>
<td valign="top">

The request was successful.



</td>
<td valign="top">

OK



</td>
</tr>
</table>

**Error Codes**


<table>
<tr>
<th valign="top">

Response Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

*400*



</td>
<td valign="top">

Bad Request



</td>
<td valign="top">

Validate JSON data. Validate that the special characters are escaped properly and new lines are added.



</td>
</tr>
<tr>
<td valign="top">

*401*



</td>
<td valign="top">

Unauthorized



</td>
<td valign="top">

The client is not authenticated.



</td>
</tr>
<tr>
<td valign="top">

*403*



</td>
<td valign="top">

Forbidden



</td>
<td valign="top">

Access to the resource is denied.



</td>
</tr>
<tr>
<td valign="top">

*404*



</td>
<td valign="top">

Not Found



</td>
<td valign="top">

The requested resource cannot be found.



</td>
</tr>
<tr>
<td valign="top">

*405*



</td>
<td valign="top">

Method Not Allowed



</td>
<td valign="top">

The requested method is not supported for the given resource.



</td>
</tr>
<tr>
<td valign="top">

*415*



</td>
<td valign="top">

Unsupported Media Type



</td>
<td valign="top">

The REST service does not support the API version requested by the REST client.



</td>
</tr>
<tr>
<td valign="top">

*500*



</td>
<td valign="top">

Internal Server Error



</td>
<td valign="top">

The operation cannot be completed due to a server error.



</td>
</tr>
<tr>
<td valign="top">

*503*



</td>
<td valign="top">

Service Unavailable



</td>
<td valign="top">

The service is currently unavailable.



</td>
</tr>
</table>

 <a name="loiod4512bcbe9c8439896e06425f247c7af"/>

<!-- loiod4512bcbe9c8439896e06425f247c7af -->

## Salutations.properties



<a name="loiod4512bcbe9c8439896e06425f247c7af__section_x1d_ndy_tjb"/>

## Salutations Default Master Data

```
0001=Ms.
0002=Mr.
```

 <a name="loio78cb6d43814c4b179eda8282c28e8d2f"/>

<!-- loio78cb6d43814c4b179eda8282c28e8d2f -->

## Functions.properties



<a name="loio78cb6d43814c4b179eda8282c28e8d2f__section_urp_3fy_tjb"/>

## Functions Default Master Data

```
1=Executive Board
2=Managing Director
4=Director
9=Project Manager
11=Manager/Head of Department
12=Team Lead/Supervisor
21=Chief Digital Officer
22=Chief Technology Officer
23=Chief Procurement Officer
24=Chief Transformation Officer
25=Chief Sales Officer
40=Employee
49=Chief HR Officer
50=Chief Information Officer
51=Chief Financial Officer
52=Chief Executive Officer
53=Chief Operating Officer
54=President
55=Vice President
56=Chief Marketing Officer
57=Consultant
59=Analyst
60=System Administrator
81=Delegate
82=Member
83=Architect
84=Developer
87=Engineer
CO=Chief Compliance Officer
```

 <a name="loiod13c638f0d5d4a8889debf278fcb0275"/>

<!-- loiod13c638f0d5d4a8889debf278fcb0275 -->

## Departments.properties



<a name="loiod13c638f0d5d4a8889debf278fcb0275__section_hj5_vfy_tjb"/>

## Departments Default Master Data

```
0002=Management
0004=Administration
0006=Training
0008=Corporate Services
0010=Information Technology
0012=SAP System Support
0020=Marketing
0030=Sales
0034=Legal
0038=Treasury
0040=Finance/Accounting
0041=Risk Management
0043=Sustainability
0048=Controlling
0049=Research/Development
0050=Human Resources
0051=Pension Fund Administration
0060=Materials Management
0062=Procurement
0065=Business Intelligence
0067=Business Planning
0070=Service
0071=Customer Services
0072=Consulting
0080=Logistics
0100=Technical Area
0101=Environmental
0110=Product Planning
0120=Engineering/Design
0160=Quality Assurance
0165=Customer Compliance Center
0170=Plant Maintenance
0200=Healthcare
0290=Operations/Manufacturing
0300=Operations/Business
0310=Administrative Board
0311=Insurance/Claims
0390=Editorial
3010=E-Commerce
3070=Real Estate Management
3110=Product Management
3150=Private Clients
3190=Health and Safety
4010=Audit
```

 <a name="loiof7eb5b72aed440fdb75657379bd368d1"/>

<!-- loiof7eb5b72aed440fdb75657379bd368d1 -->

## Relationships.properties



<a name="loiof7eb5b72aed440fdb75657379bd368d1__section_j5x_qhy_tjb"/>

## Relationships Default Master Data

```
01=Customer
02=Prospective Customer
03=Partner
04=Prospective Partner
05=Consultant
06=Press/Analyst
07=Investor/Shareholder
08=Student
09=Employee
```

 <a name="loioe62f9b8fde264f3ab644bdaa5a7876e2"/>

<!-- loioe62f9b8fde264f3ab644bdaa5a7876e2 -->

## Industries.properties



<a name="loioe62f9b8fde264f3ab644bdaa5a7876e2__section_jjp_c3y_tjb"/>

## Industries Default Master Data

```
01=Aerospace and Defense
02=Automotive
03=Banking
04=Chemicals
05=Consumer Products
06=Industrial Machinery and Components
07=Healthcare
08=High Tech
09=Insurance
10=Oil and Gas
11=Life Sciences
12=Public Sector
13=Retail
14=Telecommunications
15=Utilities
17=Building Materials
19=Forest Products, Furniture, and Textiles
21=Fabricated Metal Products
22=Primary Metals
23=Mining
25=Sports and Entertainment
27=Media
28=Passenger and Cargo Services
30=Higher Education and Research
31=Professional Services
32=Transportation (Travel and Logistics)
35=Wholesale Distribution
36=Defense
37=Engineering, Construction, and Operations
38=Postal
```

 <a name="loio3be819bd3a3a498fa287542346a7add0"/>

<!-- loio3be819bd3a3a498fa287542346a7add0 -->

## Languages.properties



<a name="loio3be819bd3a3a498fa287542346a7add0__section_ynl_n3y_tjb"/>

## Languages Default Master Data

```

AB=Abkhazian 
AA=Afar
AF=Afrikaans
SQ=Albanian
AM=Amharic
AR=Arabic
HY=Armenian
AS=Assamese
AY=Aymara
AZ=Azerbaijani
BA=Bashkir
EU=Basque
BE=Belarusian
BN=Bengali
BH=Bihari
BI=Bislama
BR=Breton
BG=Bulgarian
MY=Burmese
CA=Catalan
ZH=Chinese
zh_TW=Chinese (Taiwan)
CO=Corsican
HR=Croatian
CS=Czech
DA=Danish
NL=Dutch
DZ=Dzongkha
EN=English
EO=Esperanto
ET=Estonian
FO=Faroese
FJ=Fijian
FI=Finnish
FR=French
fr_CA=French (Caanada)
FY=Frisian
GL=Galician
KA=Georgian
DE=German
EL=Greek
KL=Greenlandic
GN=Guarani
GU=Gujarati
HA=Hausa
HE=Hebrew
HI=Hindi
HU=Hungarian
IS=Icelandic
ID=Indonesian
IA=Interlingua
IE=Interlingue
IU=Inuktitut
IK=Inupiak
GA=Irish
IT=Italian
JA=Japanese
JW=Javanese
KN=Kannada
KS=Kashmiri
KK=Kazakh
KM=Khmer
RW=Kinyarwanda
KY=Kirghiz
KO=Korean
KU=Kurdish
LO=Laotian
LA=Latin
LV=Latvian
LN=Lingala
LT=Lithuanian
MK=Macedonian
MG=Malagasy
MS=Malay
ML=Malayalam
MT=Maltese
MI=Maori
MR=Marathi
MO=Moldavian
MA=Mongolian
NA=Nauruan
NE=Nepali
NO=Norwegian
OC=Occitan
OR=Oriya
OM=Oromo
PS=Pashto
FA=Persian
PL=Polish
PT=Portuguese
pt_BR=Portuguese (Brazil)
PA=Punjabi
QU=Quechua
RM=Rhaeto-Romance
RO=Romanian
RN=Rundi
RU=Russian
SM=Samoan
SG=Sango
SA=Sanskrit
GD=Scottish Gaelic
SR=Serbian
SH=Serbo-Croatian
ST=Sesotho
TN=Setswana
SN=Shona
SD=Sindhi
SI=Sinhalese
SS=Siswati
SK=Slovak
SL=Slovenian
SO=Somali
ES=Spanish
es_MX=Spanish (Mexico)
SU=Sudanese Arabic
SW=Swahili
SV=Swedish
TL=Tagalog
TG=Tajik
TA=Tamil
TT=Tatar
TE=Telugu
GH=Thai
BO=Tibetan
TI=Tigrinya
TO=Tonga
TS=Tsonga
TR=Turkish
TK=Turkmen
TW=Twi
UK=Ukrainian
UR=Urdu
UG=Uyghur
UZ=Uzbek
VI=Vietnamese
VO=Volapuk
CY=Welsh
WO=Wolof
XH=Xhosa
YI=Yiddish
YO=Yoruba
ZA=Zhuang
ZU=Zulu
```

 <a name="loioe4e7e4c52cf04295bf94465eba7ceaaa"/>

<!-- loioe4e7e4c52cf04295bf94465eba7ceaaa -->

## Countries.properties



<a name="loioe4e7e4c52cf04295bf94465eba7ceaaa__section_ejx_s3y_tjb"/>

## Countries Default Master Data

```
AF=Afghanistan
AX=Aland Islands
AL=Albania
DZ=Algeria
AS=American Samoa
AD=Andorra
AO=Angola
AI=Anguilla
AQ=Antarctica
AG=Antigua and Barbuda
AR=Argentina
AM=Armenia
AW=Aruba
AU=Australia
AT=Austria
AZ=Azerbaijan
BS=Bahamas
BH=Bahrain
BD=Bangladesh
BB=Barbados
BY=Belarus
BE=Belgium
BZ=Belize
BJ=Benin
BM=Bermuda
BT=Bhutan
BO=Bolivia
BQ=Bonaire, Sint Eustatius and Saba
BA=Bosnia and Herzegovina
BW=Botswana
BV=Bouvet Island
BR=Brazil
IO=British Indian Ocean Territory
BN=Brunei Darussalam
BG=Bulgaria
BF=Burkina Faso
BI=Burundi
KH=Cambodia
CM=Cameroon
CA=Canada
CV=Cape Verde
KY=Cayman Islands
CF=Central African Republic
TD=Chad
CL=Chile
CN=China
CX=Christmas Island
CC=Cocos (Keeling) Islands
CO=Colombia
KM=Comoros
CG=Congo
CD=Congo DRC
CK=Cook Islands
CR=Costa Rica
CI=Côte d'Ivoire
HR=Croatia
CY=Cyprus
CZ=Czech Republic
DK=Denmark
DJ=Djibouti
DM=Dominica
DO=Dominican Republic
EC=Ecuador
EG=Egypt
SV=El Salvador
GQ=Equatorial Guinea
ER=Eritrea
EE=Estonia
ET=Ethiopia
FK=Falkland Islands (Malvinas)
FO=Faroe Islands
FJ=Fiji
FI=Finland
FR=France
GF=French Guiana
PF=French Polynesia
TF=French Southern Territories
GA=Gabon
GM=Gambia
GE=Georgia
DE=Germany
GH=Ghana
GI=Gibraltar
GR=Greece
GL=Greenland
GD=Grenada
GP=Guadeloupe
GU=Guam
GT=Guatemala
GN=Guinea
GW=Guinea-Bissau
GY=Guyana
HT=Haiti
HN=Honduras
HK=Hong Kong, China
HU=Hungary
IS=Iceland
IN=India
ID=Indonesia
IQ=Iraq
IE=Ireland
IL=Israel
IT=Italy
JM=Jamaica
JP=Japan
JO=Jordan
KZ=Kazakhstan
KE=Kenya
KI=Kiribati
KR=Korea, South
KW=Kuwait
KG=Kyrgyzstan
LA=Laos
LV=Latvia
LB=Lebanon
LS=Lesotho
LR=Liberia
LY=Libyan Arab Jamahiriya
LI=Liechtenstein
LT=Lithuania
LU=Luxembourg
MO=Macao, China
MK=Macedonia
MG=Madagascar
MW=Malawi
MY=Malaysia
MV=Maldives
ML=Mali
MT=Malta
MH=Marshall Islands
MQ=Martinique
MR=Mauritania
MU=Mauritius
YT=Mayotte
MX=Mexico
FM=Micronesia
MD=Moldova, Republic Of
MC=Monaco
MN=Mongolia
ME=Montenegro
MS=Montserrat
MA=Morocco
MZ=Mozambique
MM=Myanmar
NA=Namibia
NR=Nauru
NP=Nepal
NL=Netherlands
NC=New Caledonia
NZ=New Zealand
NI=Nicaragua
NE=Niger
NG=Nigeria
NU=Niue
NF=Norfolk Island
MP=Northern Mariana Islands
NO=Norway
OM=Oman
PK=Pakistan
PW=Palau
PS=Palestinian Territory
PA=Panama
PG=Papua New Guinea
PY=Paraguay
PE=Peru
PH=Philippines
PN=Pitcairn
PL=Poland
PT=Portugal
PR=Puerto Rico
QA=Qatar
RE=Reunion
RO=Romania
RU=Russian Federation
RW=Rwanda
SH=Saint Helena
KN=Saint Kitts and Nevis
PM=Saint Pierre and Miquelon
WS=Samoa
SM=San Marino
ST=São Tomé and Príncipe
SA=Saudi Arabia
SN=Senegal
RS=Serbia
SC=Seychelles
SL=Sierra Leone
SG=Singapore
SK=Sint Maarten
SK=Slovakia
SI=Slovenia
SB=Solomon Islands
SO=Somalia
ZA=South Africa
ES=Spain
LK=Sri Lanka
SR=Suriname
SJ=Svalbard and Jan Mayen
SZ=Swaziland
SE=Sweden
CH=Switzerland
TW=Taiwan, China
TJ=Tajikistan
TZ=Tanzania
TH=Thailand
TL=Timor-Leste
TG=Togo
TK=Tokelau
TO=Tonga
TT=Trinidad and Tobago
TN=Tunisia
TR=Turkey
TM=Turkmenistan
TC=Turks and Caicos Islands
TV=Tuvalu
UG=Uganda
UA=Ukraine
AE=United Arab Emirates
GB=United Kingdom
US=United States
UY=Uruguay
UZ=Uzbekistan
VU=Vanuatu
VA=Vatican City State
VE=Venezuela
VN=Vietnam
VG=Virgin Islands, British
VI=Virgin Islands, U.S.
WF=Wallis and Futuna
EH=Western Sahara
YE=Yemen
ZM=Zambia
ZW=Zimbabwe
```

