<!-- loio6e7543f2764f44e7ab2218c829a7cc06 -->

# View Troubleshooting Logs

Tenant administrator can filter and view troubleshooting logs directly in the administration console for SAP Cloud Identity Services to diagnose problems with authentication.



## Context

> ### Tip:  
> Use the audit logs option to track changes in the personal data.

The maximum number of log entries is 1000. The search criteria you can choose include:


<table>
<tr>
<th valign="top">

Criteria

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

Time period

</td>
<td valign="top">

The time period is in Coordinated Universal Time \(UTC\).

-   You have one hour time period for searching logs.
-   The date is limited back to 14 days from the current date

> ### Note:  
> The default selection is the current date, with a start period - one hour back from your current time in UTC.

> ### Remember:  
> The start and end periods can’t be later than the current UTC time. The end period can’t also be earlier than the start period.
> 
> The search period can’t exceed 60 minutes.



</td>
</tr>
<tr>
<td valign="top">

Severity

</td>
<td valign="top">

-   All - default
-   Error
-   Info
-   Warning



</td>
</tr>
</table>

Once you have the results you can filter them by *Time*, *Severity*, *IP Address*, *CorrelationID*, or *Message.*



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose *Monitoring & Reporting* \> *Troubleshooting Logs*.

3.  Define the criteria and start your search.

4.  Filter the search results by *Time*, *Severity*, *IP Address*, *CorrelationID*, or *Message.*.

5.  **Optional:** Export the troubleshooting logs in an Excel file.




<a name="loio6e7543f2764f44e7ab2218c829a7cc06__postreq_bml_xsy_s4b"/>

## Next Steps

-   View information about the JWT payload of the OpenID Connect tokens issued or received by Identity Authentication. For more information, see [Logging OpenID Connect Tokens](logging-openid-connect-tokens-b6c42b5.md) 


**Related Information**  


[Audit Logs](audit-logs-ad47e37.md "Tenant administrators can access the audit logs for changes in the personal data, and successful, and failed authentications in Identity Authentication.")

