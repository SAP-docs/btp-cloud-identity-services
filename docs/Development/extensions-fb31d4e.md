<!-- loiofb31d4ec2e7b43b2b7cad1dcca39634e -->

# Extensions

The Identity Directory SCIM REST API can be manually extended by adding user attribute from a custom schema. The steps include:

1.  Create custom schema in the administration console for SAP Cloud Identity Services. See [Manage Custom Schemas via Administration Console](../Operation-Guide/manage-custom-schemas-via-administration-console-d492d70.md).

    > ### Example:  
    > You have set up a scenario where Identity Authentication acts as a proxy. The default authenticating identity provider is the corporate IdP, and the *Identity Federation* option is configured for that corporate IdP.
    > 
    > Michael Adams is a user from the corporate identity provider. He is created on the proxy IdP with the custom schema `urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile` with two single-valued attributes, `birthday` and `hobby`, and the complex attribute `name` with its child attribute `firstName`.
    > 
    > > ### Sample Code:  
    > > ```
    > > {
    > >   "id": "urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile",
    > >   "schemas": [
    > >     "urn:ietf:params:scim:schemas:core:2.0:Schema"
    > >   ],
    > >   "name": "Profile",
    > >   "description": "Custom schema description",
    > >   "attributes": [
    > >     {
    > >       "name": "hobby",
    > >       "description": "Custom attribute description",
    > >       "canonicalValues": [
    > >         
    > >       ],
    > >       "multiValued": false,
    > >       "required": false,
    > >       "caseExact": false,
    > >       "type": "string",
    > >       "mutability": "readWrite",
    > >       "returned": "default",
    > >       "uniqueness": "none"
    > >     },
    > >     {
    > >       "name": "birthday",
    > >       "description": "Custom attribute description",
    > >       "canonicalValues": [
    > >         
    > >       ],
    > >       "multiValued": false,
    > >       "required": false,
    > >       "caseExact": false,
    > >       "type": "string",
    > >       "mutability": "readWrite",
    > >       "returned": "default",
    > >       "uniqueness": "none"
    > >     },
    > >     {
    > >       "name": "name",
    > >       "description": "Custom complex attribute description",
    > >       "multiValued": false,
    > >       "required": false,
    > >       "caseExact": false,
    > >       "type": "complex",
    > >       "mutability": "readWrite",
    > >       "returned": "default",
    > >       "uniqueness": "none",
    > >       "subAttributes": [
    > >         {
    > >           "name": "firstName",
    > >           "description": "Custom subAttribute description",
    > >           "canonicalValues": [
    > >             
    > >           ],
    > >           "multiValued": false,
    > >           "required": false,
    > >           "caseExact": false,
    > >           "type": "string",
    > >           "mutability": "readWrite",
    > >           "returned": "default",
    > >           "uniqueness": "none"
    > >         }
    > >       ]
    > >     }
    > >   ]
    > > }
    > > ```

2.  Assign an attribute form the custom schema to the user via one of the following options:
    -   Assign an attribute from the schema via the administration console:
        1.  *Access the administration console for Cloud Identity services* \> *Users & Authorizations* \> *User Management*.
        2.  Select a user and choose *User Details* tab.

            > ### Note:  
            > The attributes assigned from custom schema are visible at the bottom of the User Details tab under a section with the name of the custom schema.

        3.  Press the *Edit* button at the top of the page and add values to the custom schema.
        4.  Save your configuration.

            > ### Note:  
            > When the schema is assigned to the user it's in expanded mode.

            > ### Tip:  
            > To unassign the schema, remove the values of the attributes from the schema and save your changes. The schema is in collapsed mode when not assigned to a user.


    -   Assign an attribute form custom schema to the user by calling the Identity Directory SCIM REST API. See [Identity Directory Service](https://api.sap.com/api/IdDS_SCIM/path/patchUser).

        > ### Example:  
        > You have updated the Michael's `hobby` attribute, by calling the *PATCH* method of [Identity Directory Service](https://api.sap.com/api/IdDS_SCIM/path/patchUser).
        > 
        > > ### Sample Code:  
        > > ```
        > > content-type: application/scim+json
        > > 
        > > 
        > > Body:
        > > 
        > > {
        > >     "schemas": [
        > >         "urn:ietf:params:scim:api:messages:2.0:PatchOp",
        > >         "urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile"
        > >     ],
        > >     "Operations": [
        > >         {
        > >             "op": "add",
        > >             "path": "urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile:hobby",
        > >             "value": "Chess playing."
        > > 
        > >         }
        > >     ]
        > > }
        > > 
        > > ```


3.  Send the already assigned custom attribute by configuring it in the default attributes sent to the application. See [Configuring Attributes Based on Flexible Expressions](../Operation-Guide/configuring-attributes-based-on-flexible-expressions-a2f1e46.md) under the *Send Identity Directory Custom Schema Attributes* section.

    > ### Example:  
    > The default attributes for the application are configured in the administration console as follows:
    > 
    > **Default Attributes Configuration in Administration Console**
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Attribute
    > 
    > </th>
    > <th valign="top">
    > 
    > Value
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > name
    > 
    > </td>
    > <td valign="top">
    > 
    > $\{urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile.name.firstName\}
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > hobby
    > 
    > </td>
    > <td valign="top">
    > 
    > $\{urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile.hobby\}
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > birthday
    > 
    > </td>
    > <td valign="top">
    > 
    > $\{urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile.birthday\}
    > 
    > </td>
    > </tr>
    > </table>


