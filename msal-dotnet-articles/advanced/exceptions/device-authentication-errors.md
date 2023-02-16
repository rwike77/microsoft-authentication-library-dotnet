# Device authentication errors

## What are the symptoms?

You get errors like "AADSTS50097" or "Device authentication is required".

## What happens?

This error happens when a conditional access policy is applied to the resource you are accessing, which required that the device from which the token is acquired be managed by the organization, and that MSAL.NET proves this identity.

This is a conditional access policy applied by the tenant admin. For details see [How To: Require managed devices for cloud app access with Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)


## How to fix this?

To satisfy this requirement you will have to leverage WAM on Windows or the system browser (Edge on Chromium). On mobile platform, you'll need to enable the brokers (Microsoft Authenticator and Company portal)

- If you are writing a desktop application running on Windows, see [WAM integration for Desktop applications](wam). 
- [On iOS and Android](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-Docs), just [enable the broker](https://docs.microsoft.com/azure/active-directory/develop/msal-net-use-brokers-with-xamarin-apps)
- The same principles apply to Web Applications, though given you are in a browser you must leverage a browser which can “talk to” WAM (that is either Edge on Chromium or Chrome with the Azure AD extensions. For details see [Conditional access conditions | Chrome support](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-conditions#chrome-support)