<!-- loio27323219a02a44198973091169b5a5c7 -->

# View Troubleshooting Logs

Tenant administrator can view Identity Authentication troubleshooting logs to monitor the system, and diagnose and solve problems.



## Context

The maximum number of log entries is 10000. The criteria you can choose include:


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

-   1 hour - default
-   4 hours
-   24 hours



</td>
</tr>
<tr>
<td valign="top">

Severity



</td>
<td valign="top">

-   All
-   Error - default
-   Info
-   Warning



</td>
</tr>
<tr>
<td valign="top">

File format



</td>
<td valign="top">

-   JSON
-   XML
-   CSV - default



</td>
</tr>
</table>



## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Choose the *Troubleshooting Logs* tile.

3.  Define your criteria and download the log entries.




<a name="loio27323219a02a44198973091169b5a5c7__postreq_bml_xsy_s4b"/>

## Next Steps

Use the Support Log Assistant 2.0 tool to analyze your troubleshooting logs. For more information, see [Analyze Troubleshooting Logs with Support Log Assistant 2.0](analyze-troubleshooting-logs-with-support-log-assistant-2-0-72ac00b.md).

