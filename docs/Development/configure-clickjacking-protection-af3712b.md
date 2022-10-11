<!-- loioaf3712b551f042418b58f6b509bbe1ec -->

# Configure Clickjacking Protection

Clickjacking is an attempt to trick users into clicking hidden user interface elements without the user realizing it. The user thinks he or she is clicking on the underlying frame, but is actually clicking on an action chosen by the attacker.

You have two options to protect your applications against clickjacking when using embedded frames, also called overlays, for the logon pages of the applications:

-   If the applications are SAP UI5 or Web Dynpro, or they use the overlays of Identity Authentication, add the domains of these applications as trusted in the administration console for Identity Authentication. For more information, see [Configure Trusted Domains](../Operation-Guide/configure-trusted-domains-08fa1fe.md).

-   If the applications are not SAP UI5 or Web Dynpro, or they do not use the overlays of Identity Authentication, add the following code to your message handler:


> ### Sample Code:  
> ```
> 
> function messageHandler(oEvent){
>          if(oEvent.data=='SAPFrameProtection*require-origin'){
>                 oEvent.source.postMessage('SAPFrameProtection*parent-origin','*');
>          }
> }
> 
> ```

**Related Information**  


[Add Logon Overlays in Customer Applications](add-logon-overlays-in-customer-applications-5e98ecf.md "This document describes how service providers that delegate authentication to Identity Authentication can use embedded frames, also called overlays, for the logon pages of their applications.")

