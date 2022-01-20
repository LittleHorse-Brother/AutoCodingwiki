
# Framework version
- v1.1.11616.10 or higher


# Reuse connections to reduce the number of database connections used in a single request
- 修改以下几个DomainService中的Repository, 从PublicDbContext修改到BaseDbContext, 默认情况下BaseDbContext的实现类为PublicDbContext, 这样改动是为了在一个Scope里面, 可以使用BaseDbContext的实例(PublicDbContext). 使得连接可以重用
    - ContactDomainService
        - Contact
        - Contact Identity
    - ContactIdentityDomainService
        - ContactIdentity
    - DepartmentAgentDomainService
        - DepartmentAgentRelation
    - DepartmentDomainService
        - Department
    - SiteConfigDomainService
        - DepartmentConfig
        - RoleConfig
        - CreditCardMasktingConfig
        - Site
        - EnabledModule
    - VisitorDomainService
        - Vistior
    - AuditDomainService
        - AuditLog
    - EmailOutBoundQueueDomainService
        - EmailOutBoundQueue
        - EmailAttachment
        - Site
        - EmailTemplateSendSettings

- 移除GeneralDbContext, 修改以下几个DomainService中的Repository, 从GeneralDbContext修改到BaseDbContext, 理由同上
    - FeatureDomainService
        - FeaturePoint
    - ConfigurationChangeLogDomainService, 影响自动记录变更记录的功能
        - ConfigurationLog
    - OAuthClientDomainService
        - OAuthClient
    
- 移除AuthenticationDbContext, 直接使用BaseDbContext
    - 影响Basic认证相关功能

- 修改RevockedJwtDbContext， 使用完以后手动释放连接, 影响Jwt吊销检查功能

- 移除AuthorizationDbContext, 将对应实体移到PublicDbContext, 代码中直接使用BaseDbContext, 影响校验权限的功能
    - AgentPermissionRelation
    - RoleAgentRelation
    - RoleAgentRelation

- 修改BaseDbContext的默认实现为PublicDbContext， 如果其他模块有重写BaseDbContext, 请继承PublicDbContext