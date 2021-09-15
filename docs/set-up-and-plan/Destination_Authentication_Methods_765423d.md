<!-- loio765423ddb66147bc8141607a8522fe65 -->

# Destination Authentication Methods

Destinations are part of SAP BTP Connectivity and are used for communication between a cloud application and a remote system.

Destinations are required to consume a target remote service from an application. They're resolved at runtime based on their symbolic names, resulting in an object that contains customer-specific configuration details, such as the URL of the remote system or service, the authentication type, and the respective credentials.

<a name="loio765423ddb66147bc8141607a8522fe65__table_ctt_glg_l2b"/>Destination Authentication Methods on SAP BTP


<table>
<tr>
<th>

Authentication Method



</th>
<th>

Description



</th>
<th>

Environment



</th>
<th>

Internet Proxy



</th>
<th>

On-Premise Proxy



</th>
</tr>
<tr>
<td>

AppToAppSSO



</td>
<td>

Used for application-to-application communication if the caller needs to propagate its logged-in user. Both applications must be deployed on SAP BTP.



</td>
<td>

Neo



</td>
<td>

Yes



</td>
<td>

No



</td>
</tr>
<tr>
<td>

BasicAuthentication



</td>
<td>

Used for destinations that refer to a service on the Internet or an on-premise system that requires basic authentication.



</td>
<td>

Neo and Cloud Foundry



</td>
<td>

Yes



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

ClientCertificateAuthentication



</td>
<td>

Uses a technical user certificate to perform mutual transport layer security \(TLS\) authentication.



</td>
<td>

Neo and Cloud Foundry



</td>
<td>

Yes



</td>
<td>

No



</td>
</tr>
<tr>
<td>

NoAuthentication



</td>
<td>

Used for destinations that refer to a service on the Internet or an on-premise system that doesn't require authentication.



</td>
<td>

Neo and Cloud Foundry



</td>
<td>

Yes



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

OAuth2SAMLBearerAssertion



</td>
<td>

Enables applications to use SAML assertions to access OAuth-protected resources.



</td>
<td>

Neo and Cloud Foundry



</td>
<td>

Yes



</td>
<td>

Yes

> ### Note:  
> Only for Neo



</td>
</tr>
<tr>
<td>

PrincipalPropagation



</td>
<td>

Forwards the identity of an on-demand user to the Cloud Connector, and from there to the back end of the relevant on-premise system.



</td>
<td>

Neo and Cloud Foundry



</td>
<td>

No



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

OAuth2ClientCredentials



</td>
<td>

Used to request an access token from an OAuth authorization server, using the `client_credentials` grant.

The retrieved access token is cached and auto-renovated. When a token is about to expire, a new token is created shortly before the expiration of the old one.



</td>
<td>

Neo and Cloud Foundry



</td>
<td>

Yes



</td>
<td>

Yes

> ### Note:  
> Only for Neo



</td>
</tr>
<tr>
<td>

OAuth2UserTokenExchange



</td>
<td>

Using this authentication type, the destination service performs all the user token exchange steps automatically, which lets you simplify your application development.

This enables you to use a user token that you already have, in order to fetch a token from a different OAuth client, in the context of the same tenant.



</td>
<td>

Cloud Foundry



</td>
<td>

Yes



</td>
<td>

No



</td>
</tr>
<tr>
<td>

OAuth2Password



</td>
<td>

Provides support for applications to use the OAuth password grant flow for consuming OAuth-protected resources.



</td>
<td>

Cloud Foundry



</td>
<td>

Yes



</td>
<td>

No



</td>
</tr>
<tr>
<td>

OAuth2JWTBearer



</td>
<td>

To allow an application to call another application, pass the user context, and fetch resources, the caller application must pass an access token. In this authorization flow, the initial user token is passed to the OAuth server as input data. This process is performed automatically by the destination service, which helps to simplify application development.

This enables you to use a user token that you already have, in order to fetch a token from a different OAuth client, in the context of the same tenant.



</td>
<td>

Cloud Foundry



</td>
<td>

Yes



</td>
<td>

No



</td>
</tr>
<tr>
<td>

SAMLAssertion



</td>
<td>

Retrieves a generated SAML assertion from the destination service.



</td>
<td>

Cloud Foundry



</td>
<td>

Yes



</td>
<td>

Yes



</td>
</tr>
</table>

> ### Recommendation:  
> For user token exchange, use the OAuth2JWTBearer authentication method when possible, as OAuth2UserTokenExchange needs a two-step mechanism to achieve the same resolution.
> 
> Avoid using BasicAuthentication and OAuth2Password in production environments. However, they work well for test environments.
