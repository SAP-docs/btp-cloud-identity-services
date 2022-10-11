<!-- loio066bda825cb148629aa1934b770eb4ed -->

# Getting Started with the Identity Service of SAP BTP

To create OpenID Connect \(OIDC\) applications in the Identity Authentication service using SAP Cloud Service Management service, instantiate the Identity service and bind your service instance to an application. The Identity service automates the manual creation of Identity Authentication OIDC applications.



<a name="loio066bda825cb148629aa1934b770eb4ed__prereq_u31_tfg_wnb"/>

## Prerequisites

-   You've established trust between your subaccount and your tenant of the Identity Authentication service using OpenID Connect.

    For more information, see [Establish Trust and Federation Between UAA and Identity Authentication Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/161f8f0cfac64c4fa2d973bc5f08a894.html).

-   You've prepared your application to consume services of SAP BTP

    For more information, see [Consuming Services in Other Environments Using the Service Management Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).




## Context

You can use Service Manager capabilities to create and manage instances of the Identity service from any runtime environment.

In the following procedure, we provide the syntax using the Cloud Foundry command-line interface \(cf cli\) and the Kubernetes command-line tool \(kubectl\).



## Procedure

1.  Create the identity instance.

    The following examples

    -   cf cli: ***cf create-service identity application *<instance\_name\>****
    -   kubectl:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: servicecatalog.k8s.io/v1beta1
        kind: ServiceInstance
        metadata:
          name: {<instance_name>}
          namespace: {<namespace>}
        spec:
          clusterServiceClassExternalName: identity
          clusterServicePlanExternalName: application
        EOF
        ```


2.  Bind your service instance to your application.

    -   cf cli: ***cf bind-service *<my\_app\_name\>* *<instance\_name\>****
    -   kubectl:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: servicecatalog.kyma-project.io/v1alpha1
        kind: ServiceBindingUsage
        metadata:
         name: {<instance_name>}
         namespace: {NAMESPACE_NAME}
        spec:
         serviceBindingRef:
           name: {<binding_name>}
         usedBy:
           kind: deployment 
           name: {<my_app_name>}
         parameters:
           envPrefix:
             name: "PREFIX_"
        EOF 
        ```


3.  Consume the binding data.


    <table>
    <tr>
    <th valign="top">

    Binding data consumed by a …


    
    </th>
    <th valign="top">

    Then …


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    **Web application**


    
    </td>
    <td valign="top">

    Use the approuter to authenticate the user. Otherwise, authenticate the user in the application code, according to the OIDC specification using information from service binding \(URL, client credentials\). For more information, see:

    -   [@sap/approuter](https://www.npmjs.com/package/@sap/approuter) at *npm*.

        > ### Note:  
        > Application router support for the Identity service is currently in beta.

    -   [Basic Client Implementer's Guide](https://openid.net/specs/openid-connect-basic-1_0.html) at *OpenID*.



    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Service consumed by application \(principal propagation\)**


    
    </td>
    <td valign="top">

    Validate the token validation and evaluate the binding data using client libraries.

    For more information, see [Reference Information for the Identity Service of SAP BTP](reference-information-for-the-identity-service-of-sap-btp-9379444.md).


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Using Services in the Kyma Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ea4dd81e49254dd482d32e3c20f4477a.html)

