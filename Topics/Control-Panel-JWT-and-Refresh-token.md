We use JWT to authenticate the login agent. The token is saved in a cookie named `token_{siteId}`.

There is another cookie named `tokenExpire_{siteId}` which contains the expiration time of the token. This is for the token refreshing.

Front end application needs to refresh the token before expiration if there are user activities (switching between pages) on the browser page. 

The refresh token is done via Axios middleware (code located in @comm100/framework library's `RefreshToken.ts` file), before sending each request it will ask the middleware first, the middleware will check if it is time to refresh the token and send a refresh token request if it is. 

Every `UIProject` must install the middleware during the startup process: call the `startRefreshToken` method of the `TokenDomainService` class inside the `main` function.




