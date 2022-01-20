This section mainly introduces the branding information related to the control panel. Branding includes the following information:
- [Favicon](#favicon)
- [Logo](#logo)
- [Theme](#theme)
- [Branding Name](#branding-name)
- [Product Name](#product-name)
- [Help Text](#help-text)

## Prepare
The API for obtaining branding information has been prepared. The data is saved in `GlobalSettings` and obtained through `useBrandConfig`.

endpoint: `/api/global/partnerBrandConfig`
method: `GET`
data:
```
{
  controlPanelLogoCodeSnippet: string; it is the HTML content of the logo
  brandingName: string; the name of partner
  pageColor: string; the base color of page content
  navigationColor: string; the base color of menu
  ...
}
```

## Favicon
Favicon will be displayed on the browser. If the web page is opened use window modal, it will be displayed in the upper left corner of the window. If the web page is opened in the form of tab, it will be displayed on the left side of the tab. The resource path of favicon is fixed. The backend service needs to intercept the request and obtain the corresponding resources according to the requested domain.

Favicon's url：`/favicon.png`

## Logo
If the `controlPanelLogoCodeSnippet` is provided, use it as `Logo`, otherwise use comm100 logo as default.

## Theme
Calculate the color system related to the theme according to the provided color. At present, the `controlpanel` is divided into two color systems as follows, which are calculated according to the formula provided by the UX team.
- page content color system
- menu color system

### Related components and methods of generating theme
- CTheme
- CThemeProvider
- theme method

#### CTheme
`CTheme` component uses two components `CssBaseLine` and `CThemeProvider` in the framework module. This component is only allowed to be used at the root node, and it will generate style tags. 

![image.png](/.attachments/image-714f562f-e1fb-4249-af87-828ccf0d89a9.png)


#### CThemeProvider
In the framework module, `CThemeProvider` uses `useBrandConfig` to obtain the branding info, and calculates the `Theme` assigned to theme context by the [`theme`](#them-method) method

#### theme method
The theme method in the `StyledComponents` module. it has two optional parameters, base on parameters return the `Theme` object, The theme color of comm100 is used by default.

Signature： `theme(language?: string, baseColors?: BaseColors): Theme`
params：
- `language`: string, the currently selected language, default is English. Different language styles may be different.
- `baseColors`: The currently configured base colors, default is the base colors of comm100.
  - pageColor: string, the base color of the page content
  - navigationColor: string, the base color of the menu

![image.png](/.attachments/image-9912c2b4-5b6a-4237-9494-b40fe2bf2c22.png)

## Branding Name

Below is the [IP Allowlist](https://dash11.comm100.io/ui/10100000/global/security/ipallowlist/loginipallowlist/) page description.

old:
`Control access to the Comm100 Control Panel and Agent Console by restricting logins to specific IPs.`
new:
`Control access to the @brandConfig.brandingName Control Panel and Agent Console by restricting logins to specific IPs.`

## Product Name

Partner can customize product name. So keywords about product name in the text of UI should be replaced with definitions of the corresponding partner.

For example:

![image.png](/.attachments/image-419b82cf-2573-44b5-994d-77e4f32114f8.png)
 
We should configure the lable of  `Agent Assist` to `@brandCondig.partnerModuleRebrandingNames.agentAssist`. The system will automatically parse this variable and replace it with the value in the corresponding object values.


## Help Text

For some partners, some help texts in products may not need to be displayed, mainly because they do not have corresponding KB articles, so we need to configure not to display that part of content.

For example:

![image.png](/.attachments/image-419b82cf-2573-44b5-994d-77e4f32114f8.png)

For the description we can configure it as `@brandConfig.partnerModuleRebrandingNames.agentAssist can provide different answer suggestions to agents when a visitor sends a question. Agents can select to use one of the answer suggestions. @inAppUiHelpText.helper_agent_assist_more_details` in auto coding. And the helper text with key `helper_agent_assist_more_details` in partner should configure to `For more details, read this <a href="https://portal2.comm100.io/kb/10000/6486ce9b-d54e-458d-89ac-5b5fdaa17774/a/bde4a989-470b-4b77-81c9-6e3ae26df293/understanding-agent-assist" target="_blank">Knowledge Base article</a>.` for Comm100. Others can configure to empty.

