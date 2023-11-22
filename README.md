# Recco Web Version

Recco is a health recommendation tool, that can be integrated in your own web- or smartphone application.
Get in contact by following this link: https://www.significo.com/recco

## Setup

### Within the Recco Backoffice
* Log in to the [Recco Backoffice](https://recco-admin.significo.dev/) and follow the steps to configure you application
* Create an _App-Token_ within the Recco Backoffice, copy it and keep it safe

### In your web-application

In order to give your users the opportunity to sign up to the web-version of Recco,
you need to link it in your web-app.
For authentication, Recco expects a session token as query param in the URL:

`https://recco-web.significo.app?session-token=[YOUR_TOKEN]`

#### Create Session Token

**Step 1:** Call `POST https://recco-api.significo.dev/api/v1/app_users/transient_tokens`

Add an `Authorization` header to this request and add your _App-Token_ there (the token you received in the Recco Backoffice):  
`Authorization: Bearer [YOUR_APP_TOKEN]`

As response, you will get an `Access-Token`.

**Step 2:** Call `https://recco-api.significo.dev/api/v1/app_users/tokens`

Add an `Authorization` header to this request and add your _Access-Token_ there (the token you received in the request before):  
`Authorization: Bearer [YOUR_ACCESS_TOKEN]`

Add also `Client-User-Id` to the request header. That `ID` will Recco use to identify the user, that wants to use Recco.    
`Client-User-Id: [ID]`

As response, you will get an `Session-Token`. The `Session-Token` can be added as query-param to the Recco URL in order to sign in to the web version of Recco.


### URL Query Params
* `session-token`: For authentication of the user.
* `lang` _(optional)_: Determine the application language. Currently supported are `en` and `de`. If omitted, the browser language will be used. 
