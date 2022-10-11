<!-- loio61d3a864fc0544498627e5554bc929d9 -->

# Configuring Terms of Use

You can configure a custom terms of use document by creating a new document, adding and editing its language versions, and defining the document for an application.

Every time you want to update the terms of use document you add a new language versions for the document.

Each terms of use document can have one draft and one active version. You can view all language version in the administration console. Optionally you can edit the draft version of a document before making it an active version.

Once a terms of use document is created it can't be renamed.

For each language version, you have to upload a text file. You can define a terms of use document in the following languages:

Arabic, Azerbaijani, Bulgarian, Catalan, Chinese \(PRC\), Chinese \(Taiwan\), Croatian, Czech, Danish, Dutch, English \(United Kingdom\), English \(United States\), Estonian, Finnish, French \(Standard\), French \(Canada\), German \(Standard\), Greek, Hebrew, Hungarian, Italian, Japanese, Korean, Latvian, Norwegian, Polish, Portuguese \(Portugal\), Romanian, Russian, Serbian, Slovak, Slovenian, Spanish \(Spain\), Spanish \(Mexico\), Swedish, Turkish, Ukrainian, Welsh.

The language is defined in the following order of importance:

-   By the `locale` parameter in the URL used for accessing the application.

    > ### Note:  
    > If the SP is configured to support a specific language, only this language is used by the application.

-   By the language of the application's browser.

    > ### Note:  
    > The application takes the browser language only if the SP's language is not selected, and the `locale` parameter isn’t set in the URL. The default browser setting is *English*.


> ### Note:  
> If there is only one language for the document, it is recommended to be *English \(United States\)*.
> 
> If the languages are more than one, one of them must be *English \(United States\)*.

To configure terms of use in the administration console, do the following:

