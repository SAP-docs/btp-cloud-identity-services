<!-- loio38baa251132c4b088f41261fb3158fb3 -->

# Data Control Language for SAP BTP

Developers define rules and authorization policies in SAP Cloud Identity Services. They use an SQL-like language - the data control language \(DCL\). Administrators can combine these rules within authorization policies and assign them to users.



<a name="loio38baa251132c4b088f41261fb3158fb3__section_dft_thn_5pb"/>

## Prerequisites

The following services must be activated in your Cloud Foundry SAP BTP subaccount. Check your services in your subaccount by using `cf marketplace` in the Cloud Foundry command line.

-   The Authorization Management service provides the `authorization` service in the Cloud Foundry marketplace.

-   The Cloud Identity service provides the `identity` service in the Cloud Foundry marketplace. This means that the subaccount is enabled. It has an SAP Cloud Identity Services tenant, which provides the zone.




Using this language, developers define authorizations. Administrators can refine them by combining rules within authorization policies. In the administration console, they assign the authorization policies to users.

This is what a policy definition looks like.

> ### Note:  
> Choose the links in the sample code. They take you to a description of the DCL elements.

> ### Sample Code:  
> ```
> {
>  <?sap-ot O2O class="- topic/xref " href="dd915846c40b41ceb248c48f6a3ad90a.xml" text="schema" desc="" xtrc="xref:1" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/38baa251132c4b088f41261fb3158fb3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  {
> 	SalesOrderType: number
> }
>  <?sap-ot O2O class="- topic/xref " href="dd915846c40b41ceb248c48f6a3ad90a.xml" text="POLICY" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/38baa251132c4b088f41261fb3158fb3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  readSalesOrders_Type {
> 	 <?sap-ot O2O class="- topic/xref " href="dd915846c40b41ceb248c48f6a3ad90a.xml" text="GRANT" desc="" xtrc="xref:3" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/38baa251132c4b088f41261fb3158fb3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  read ON  <?sap-ot O2O class="- topic/xref " href="dd915846c40b41ceb248c48f6a3ad90a.xml" text="salesOrders" desc="" xtrc="xref:4" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/38baa251132c4b088f41261fb3158fb3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>   <?sap-ot O2O class="- topic/xref " href="dd915846c40b41ceb248c48f6a3ad90a.xml" text="WHERE" desc="" xtrc="xref:5" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/38baa251132c4b088f41261fb3158fb3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>   <?sap-ot O2O class="- topic/xref " href="dd915846c40b41ceb248c48f6a3ad90a.xml" text="SalesOrderType" desc="" xtrc="xref:6" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/38baa251132c4b088f41261fb3158fb3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  BETWEEN 100 AND 500;
> }
> ```

