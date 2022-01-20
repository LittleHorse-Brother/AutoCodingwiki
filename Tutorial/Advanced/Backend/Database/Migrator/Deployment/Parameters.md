## Automatically generated parameters 

All automatically generated parameters will be automatically generated based on the deployment name and base domain name, and it is generally not recommended to manually pass in. 

For example: the deployment name is partner4 and the base domain name is comm100dev.io, then CenterPortalUrl will be automatically generated as https://partner4center.comm100dev.io, and InternalPortalUrl will be automatically generated as https://partner4internal.comm100dev.io, and so on analogy. 

{CenterPortalUrl}=https://{deploymentName}center.{baseDomainName}

{InternalPortalUrl}=https://{deploymentName}internal.{baseDomainName}

{PartnerPortalUrl}=https://{deploymentName}partner.{baseDomainName}

{MessagingProxyUrl}=https://messagingProxy.{baseDomainName}

{CommonServiceUrl}=https://commonservice.{baseDomainName}

{PciFormUrl}=https://pciform.{baseDomainName}


{PlatformPortalUrl}=https://{deploymentName}dash.{baseDomainName}

{PlatformApiUrl}=https://{deploymentName}api.{baseDomainName}

{PlatformStandbyServerUrl}=https://{deploymentName}max.{baseDomainName}

{PlatformFileServiceServerUrl}=https://{deploymentName}file.{baseDomainName}

{PlatformFileStandbyServiceServerUrl}=https://{deploymentName}filestandby.{baseDomainName}

{PlatformChatServerUrl}=https://{deploymentName}chatserver.{baseDomainName}

{PlatformChatMaximumOnServerUrl}=https://{deploymentName}max.{baseDomainName}/ChatServer


{RouterServerUrl}=https://{deploymentName}vue.{baseDomainName}

{RouterStandbyServerUrl}=https://{deploymentName}vuemax.{baseDomainName}


{VueServerUrl}=https://{deploymentName}vue.{baseDomainName}

{VueStandbyServerUrl}=https://{deploymentName}vuemax.{baseDomainName}

{JwtPrivateKeyPath}=https://jwttoken.{baseDomainName}/jwt-cert.pfx

## Others

{SiteIdentitySeed}=1000

{PlanIdentitySeed}=1000

{PartnerIdentitySeed}=100000

{PlatformId}=100

{JWTPublicKey}=MIIC3jCCAcagAwIBAgIQGO3nMcU0ObFKSsT/wML3ATANBgkqhkiG9w0BAQUFADAY  MRYwFAYDVQQDEw1XSU4tSG9zdGVkMTkwMB4XDTE5MDUxNzAzMDAyNloXDTIwMDUx  NzAwMDAwMFowGDEWMBQGA1UEAxMNV0lOLUhvc3RlZDE5MDCCASIwDQYJKoZIhvcN  AQEBBQADggEPADCCAQoCggEBAPmW73sDXSPxoMtH8qIMQJ8nW2fQIjzqpzKR4P8X  DAdmesSqIaQRFc9KeXxyPa1Pf6B4BSCMP84h8sp/hMBO7UfT760eqex5vMeOG4jI  l4t5jJ9sYtI/66lJ8suryGNjPUT7swxNbDDK1CxFNadm9Vv7CGaqozg4DqjADy/o  w4/hr9+HfzePWy++pTSmtppRQ0663WR8duVOtciQgmcsWnfX7NbGmp7/9db5sffG  smiV1Oty+6EfLtHNq3NcTehAAqK9YyJyiGbd13hpkyUD9r9i9knDX5iYsjuD7jCq  JwFy01bt7v2G9ss9+dLY8wnLXcQi7sHB9bc8bhRXYxhY5zUCAwEAAaMkMCIwCwYD  VR0PBAQDAgQwMBMGA1UdJQQMMAoGCCsGAQUFBwMBMA0GCSqGSIb3DQEBBQUAA4IB  AQALc+H4gelYHhGJxYnlgghj7GCfUMUdjAxOUBUMItd3NHC2H/LF1KvI5Whi38KJ  8ioO4VHsx5kudE6BTahMLyCa6SPPKKEth5CnkMGdGnInh0vX4DHpymVCI/7H1Y1O  FTsSnIifaq2ywXw2ezcRwp0KTaI7DGmJDp6TvgakfS2LrA3YvhT7wA7KReSoul4B  P9NzV5ORY+eL7l7y45fqmFybZ/+k5r6lh3xKIvf9kmuVPegzEcWL3Zoh3Egft3Kq  6in7qzpGNtRJCD3eWUABi6dTf1C4VI+8IGs9AkzyT9TIsunUKq6+lhdwwCfI79IO  oVS1C9yeZlkurFeGppfo+PyV

Note that this parameter only needs to be passed in the CERTIFICATE part when passing in, -----BEGIN CERTIFICATE----- and -----END CERTIFICATE----- will be automatically added 

{JwtPrivateKeyPassword}=Aa000000

