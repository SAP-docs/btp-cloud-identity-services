<!-- loio0d90e3454a9d418a9c2117321e9e52c2 -->

# Glossary for Data Protection and Privacy

The following terms are general to SAP products. Certain terms might not be relevant for Identity Authentication.




<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Definition



</th>
</tr>
<tr>
<td valign="top">

**Blocking** 



</td>
<td valign="top">

A method of restricting access to data for which the primary business purpose has ended.



</td>
</tr>
<tr>
<td valign="top">

**Business purpose** 



</td>
<td valign="top">

A legal, contractual, or in other form justified reason for the processing of personal data. The assumption is that any purpose has an end that is usually already defined when the purpose starts.



</td>
</tr>
<tr>
<td valign="top">

**Consent** 



</td>
<td valign="top">

The action of the data subject confirming that the usage of his or her personal data shall be allowed for a given purpose. A consent functionality allows the storage of a consent record in relation to a specific purpose and shows if a data subject has granted, withdrawn, or denied consent.



</td>
</tr>
<tr>
<td valign="top">

**Deletion** 



</td>
<td valign="top">

Deletion of **personal data** so that the data is no longer available.



</td>
</tr>
<tr>
<td valign="top">

**End of business** 



</td>
<td valign="top">

Date where the business with a data subject ends, for example the order is completed, the subscription is canceled, or the last bill is settled.



</td>
</tr>
<tr>
<td valign="top">

**End of purpose \(EoP\)** 



</td>
<td valign="top">

End of purpose and start of blocking period. The point in time, when the primary processing purpose ends \(for example contract is fulfilled\).



</td>
</tr>
<tr>
<td valign="top">

**End of purpose \(EoP\) check** 



</td>
<td valign="top">

A method of identifying the point in time for a data set when the processing of **personal data** is no longer required for the primary **business purpose**. After the **EoP** has been reached, the data is **blocked** and can only be accessed by users with special authorization \(for example, tax auditors\).



</td>
</tr>
<tr>
<td valign="top">

**Personal data** 



</td>
<td valign="top">

Any information relating to an identified or identifiable natural person \("data subject"\). An identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural, or social identity of that natural person



</td>
</tr>
<tr>
<td valign="top">

**Purpose**



</td>
<td valign="top">

The information that specifies the reason and the goal for the processing of a specific set of personal data. As a rule, the purpose references the relevant legal basis for the processing of personal data.



</td>
</tr>
<tr>
<td valign="top">

**Residence period** 



</td>
<td valign="top">

The period of time between the end of business and the end of purpose \(EoP\) for a data set during which the data remains in the database and can be used in case of subsequent processes related to the original purpose. At the end of the longest configured residence period, the data is blocked or deleted. The residence period is part of the overall retention period.



</td>
</tr>
<tr>
<td valign="top">

**Retention period** 



</td>
<td valign="top">

The period of time between the end of the last business activity involving a specific object \(for example, a business partner\) and the deletion of the corresponding data, subject to applicable laws. The retention period is a combination of the residence period and the blocking period.



</td>
</tr>
<tr>
<td valign="top">

**Sensitive personal data** 



</td>
<td valign="top">

A category of personal data that usually includes the following type of information:

-   Special categories of personal data, such as data revealing racial or ethnic origin, political opinions, religious or philosophical beliefs, trade union membership, genetic data, biometric data, data concerning health or sex life or sexual orientation.
-   Personal data subject to professional secrecy
-   Personal data relating to criminal or administrative offenses
-   Personal data concerning insurances and bank or credit card accounts



</td>
</tr>
<tr>
<td valign="top">

**Where-used check \(WUC\)** 



</td>
<td valign="top">

A process designed to ensure data integrity in the case of potential blocking of business partner data. An application's where-used check \(WUC\) determines if there is any dependent data for a certain business partner in the database. If dependent data exists, this means the data is still required for business activities. Therefore, the blocking of business partners referenced in the data is prevented.



</td>
</tr>
</table>

