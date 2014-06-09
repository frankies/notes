##   	Notes of OAuth2 study  ##
 
**1. Grant type**

- client_credentials
- authorization_code
- implicit
- password
- refresh_token
 

**2. Authentication Scheme**

- form
- query
- header

**3. The grant type and response token access provider**

>Base interface : org.springframework.security.oauth2.client.token.AccessTokenProvider

- AuthorizationCode:	
 
>`org.springframework.security.oauth2.client.token.gran	t.code.AuthorizationCodeAccessTokenProvider`
 
- ClientCredentials

  >`org.springframework.security.oauth2.client.token.grant.client.ClientCredentialsAccessTokenProvider`

- Implicit

  >`org.springframework.security.oauth2.client.token.grant.implicit.ImplicitAccessTokenProvider`

- Password

>`org.springframework.security.oauth2.client.token.grant.password.ResourceOwnerPasswordAccessTokenProvider`
 


**4. Key class or methods of client-side**

- Request authorization code
 
>`org.springframework.security.oauth2.client.OAuth2RestTemplate.acquireAccessToken(OAuth2ClientContext)`


**5. Key class or methods of server-side**
 
 - Authorization code process endpoint (Context path `/oauth/authorize` "![AuthorizationEndpoint](pic/authoiztionEndpoint.png)

> `org.springframework.security.oauth2.provider.endpoint.AuthorizationEndpoint`

 
- Spring security filter chain 
  
   see ![SpringSecurityFilterChain](pic/SpringSecurityFilterChain.png )
 

- Password encoder

  <1> PlaintextPasswordEncoder

  <2> Md5PasswordEncoder

  <3> ShaPasswordEncoder

- Token endpoint of resource server side.

 - **Supper class** :
 `org.springframework.security.oauth2.provider.endpoint.AbstractEndpoint`

 - **Subclass** : 
  	
	`org.springframework.security.oauth2.provider.endpoint.AuthorizationEndpoint`("***/oauth/authorize***")
    
	`org.springframework.security.oauth2.provider.endpoint.TokenEndpoint`("***/oauth/token***")

- Token granter
 - Interface : `org.springframework.security.oauth2.provider.TokenGranter`  
 
- Key generator of token store
 
	`org.springframework.security.oauth2.provider.token.DefaultAuthenticationKeyGenerator`

	![DefaultAuthenticationKeyGenerator](pic/default_authentication_key_generator.png)


- The previous request store and restore in session

  -	Save in session when it's not 'stateless' and 'AuthenticationException' type exception occurses in the web proccessing.
  	
![Save request](pic/storeRequest.png)


  -	Restore the request from session
  
![Restore request](pic/restoreRequest.png)


**6. Main key points**

- How `ProviderManager` to created? ![Answer](pic/HowProviderManagerCreated.png) 
