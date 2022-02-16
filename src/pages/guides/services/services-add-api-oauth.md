# Add API to project using OAuth

Adding an API to an empty project is the same whether you are working in a personal or enterprise project. Adding an API to a templated project is similar, with one small variation: APIs are added to individual workspaces, not to the project as a whole.

To begin adding an API from within a templated project, first select the appropriate workspace to open the *Workspace overview*. Then, select **+ Add Service** in the left navigation and choose **API** from the dropdown. 

In an empty project, select **+Add to Project** in the left navigation of the *Project overview* and then choose **API**, or select **Add API** from the quick start buttons.

![](../../images/services-add-to-project.png)

## Add an API

Using REST APIs allows your application to make calls to Adobe services and products. The *Add an API* dialog shows a list of available services with the default *View by* setting to show only those services available to you.

<InlineAlert slots="text"/>

Many services are only available through paid licenses or subscriptions. Licenses and subscriptions can refer to either your organization or your personal licenses if you are building a personal project. For this reason, if you select "All" from the *View by* dropdown, you may notice that several services appear greyed out in the list. If you believe that you should have access to one of these disabled services, please speak with your system administrator or Adobe sales representative.

Once you have found and chosen an API that you would like to add, select **Next** to begin configuring the API.

![](../../images/services-api-oauth-select.png)

## Configure API

User authentication using OAuth allows your end users to sign in to your integration with an Adobe ID. With an OAuth token, your integration will be able to access Adobe services and content on behalf of the logged in user. For more information, read the [OAuth Authentication and Authorization documentation](../authentication/OAuth/index.md).

To configure an API using OAuth 2.0 authentication and authorization, you must first select the platforms where you want to use this integration: Web App, Single Page App, or Native App. 

<InlineAlert slots="text"/>

Depending on the selected API, some of the platforms may not be available to be used with that API. If more than one platform is available, select the platform that best suits your application use case.

TODO
![](../../images/services-api-oauth-configure.png)

Depending on the platform(s) you select, you may be required to provide additional configuration information:

### Web App

The Web App platform is best suited for applications that have a backend server. OAuth credentials for Web App require the application to securely store a client secret on the backend server. With the use of the client secret the application can then fetch tokens on the backend server and not risk exposing the client secret or the tokens through the frontend application.

In OAuth 2.0 standard terminology, an OAuth credential for the Web App platform is a *confidential* client with a HTTPS redirect.

When setting up an OAuth credential for the Web App platform you are required to provide:
1. [A default Redirect URI](#oauth-20-default-redirect-uri) 
2. [A Redirect URI pattern](#oauth-20-redirect-uri-pattern)

### Single Page App

The Single Page App platform is best suited for JavaScript based applications that run in the browser that either do not have a backend server or want to fetch tokens on the frontend. OAuth credentials for Single Page Apps do not require the application to store a client secret, and therefore, must utilize the [OAuth 2.0 PKCE flow](https://oauth.net/2/pkce/) to securely obtain tokens.

In OAuth 2.0 standard terminology, an OAuth credential for the Single Page App platform is a *public* client with a HTTPS redirect.

When setting up an OAuth credential for the Single Page App platform you are required to provide:
1. [A default Redirect URI](#oauth-20-default-redirect-uri) 
2. [A Redirect URI pattern](#oauth-20-redirect-uri-pattern)


### Native App

The Native App platform is best suited for applications that run natively on a device (Android, iOS, Windows, Mac, and others)that either do not have a backend server or want to fetch tokens on the frontend. OAuth credentials for Native Apps do not require the application to store a client secret, and therefore, must utilize the [OAuth 2.0 PKCE flow](https://oauth.net/2/pkce/) to securely obtain tokens.

In OAuth 2.0 standard terminology, an OAuth credential for the Native App platform is a *public* client with a non-HTTPS redirect.

### OAuth 2.0 Default Redirect URI

A *Default redirect URI* is the URL of the page or script (usually at the root of your web app) that Adobe will access during the authentication process. It can contain a maximum of 256 characters and cannot be a regular expression.

<InlineAlert slots="text"/>

The *Default redirect URI* MUST be hosted on a secure server (HTTPS), even if it is only a localhost instance. For example, **https://redirect.com/uri/etc**. 

### OAuth 2.0 Redirect URI pattern

When creating a new authorize request, the OAuth 2.0 framework allows your application to request a different redirect URI than the default Redirect URI. However, any requested redirect URI would be matched against the *Redirect URI pattern* you supply. The authorize request can be successfully completed only if the requested redirect URI passes regex matching, 

A *Redirect URI pattern* is a URI path (or comma-separated list of paths) to which Adobe can redirect (if requested) when the login flow is complete. It must be within your application domain, and is typically the root. It can contain a maximum of 512 characters.

<InlineAlert slots="text"/>
  
You must escape periods (**.**) with **\\**. For example, **https://example\\.com/**.

### Web

The OAuth credential for the Web platform has been deprecated in favor of the [Web App platform](#web-app). Furthermore, the new Web App platfotm credentials do not support the weaker OAuth implicit flow. Applications looking for a substitute for the OAuth implicit flow should use the more secure [Single Page App platform](#single-page-app).

### iOS

The OAuth credential for the iOS platform has been deprecated in favor of the [Native App platform](#native-app).
### Android

The OAuth credential for the Android platform has been deprecated in favor of the [Native App platform](#native-app).


## API overview

With the API configured, you are redirected to the API overview, providing links to documentation, the ability to download files in order to experiment with the API using Postman, and the *Credential details* including the *Redirect URI* that you just provided.

You can also elect to remove the API on this screen using the **Remove API** button in the top-right corner.

![](../../images/services-api-oauth-added.png)

## Credentials

Now that you have added an API, you can return to the *Project overview* (or *Workspace overview* in a templated project) at any time to view the details for that API and any other project services you may have added. 

You can select the specific API from the left navigation to view its details or remove the API using the **Remove API** button in the top-right corner.

You can also select the specific credential type from under *Credentials* in the left navigation to view the *Credential details* and perform other actions (view Client ID, retrieve client secret, etc.) as needed. For more information on accessing credentials, please read the [credentials overview](../credentials.md).

## Insights

Adobe Developer Console automatically generates valuable insights related to API usage for each enterprise project (or individual workspace when working in a templated project), as well as for each personal project, including XD Plugins.

To learn more about insights, begin by reading the [insights overview](../insights.md).

## Next steps

With an API successfully added, you can follow the same workflow steps to add additional APIs, or return to the [services overview](../services/index.md) to select another type of service to add to your project.

If you have completed development on your project and are ready to submit your application for approval, please read the [project approval guide](../projects/approval.md) to get started.


