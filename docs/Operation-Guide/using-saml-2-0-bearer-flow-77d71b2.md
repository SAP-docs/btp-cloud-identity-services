<!-- loio77d71b2fd26646c9b2119620412805d9 -->

# Using SAML 2.0 Bearer Flow

To authenticate using the SAML 2.0 Bearer flow, follow these procedures. Tasks 1 and 2 are configurations on the Identity Authentication side. Task 3 is a configuration on the client \(relying party\) side.

Use this flow to exchange a SAML assertion from your corporate identity provider for an OAuth token. This flow implements [RFC 7522](https://datatracker.ietf.org/doc/html/rfc7522).

Your implementation must include the following requirements:

-   The issuer of the SAML assertion must match the name of a trusted SAML corporate identity provider.

-   The SAML audience must specify the Identity Authentication issuer.

    <code>&lt;saml:Audience&gt;https://<i class="varname">&lt;IAS_Issuer&gt;</i>.<i class="varname">&lt;domain&gt;</i>&lt;/saml:Audience&gt;</code>

-   In the `subject` element, the `subjectConfirmation` uses the method `urn:oasis:names:tc:SAML:2.0:cm:bearer`. In this element, `SubjectConfirmationData` specifies the recipient as the Identity Authentication issuer combined with the token path.

    > ### Example:  
    > ```
    > 
    > <saml:Subject>
    >     <saml:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress">my.name@example.com</saml:NameID>
    >     <saml:SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
    >         <saml:SubjectConfirmationData NotOnOrAfter="2026-03-24T11:42:49Z" Recipient="https://my_issuer.cloud.sap/oauth2/token"/>
    >     </saml:SubjectConfirmation>
    > </saml:Subject>
    > ```


