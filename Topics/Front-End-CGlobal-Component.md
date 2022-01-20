Control panel use React's [Context](https://reactjs.org/docs/context.html#gatsby-focus-wrapper) feature to provide global data. It contains configs, current site info, current agent info, etc.

## Provider

`CGlobal` component contains a set of react context providers:
   - GlobalSettingsProvider
      - configs: global configs like file service url
      - site: current site info
      - currentAgent: current agent info
      - entityVariables: variables referenced from auto coding configurations (conditionForShowing etc.).
      - brandingConfig: parent partner customize child partner's theme or other info.
   - LocalizationProvider: timezone, language related configs
   - ThemeProvider: meterial-ui theme
   - IconProvier: svg icon list, come from auto coding db's dbo.t_autocoding_icon table.

## Consumer
Underhood, all react contexts are consumed by the `useContext` hook. We have encapsulated some custom hooks and components on top of it:

- useCurrengAgent
  Get current agent
- useBrandConfig
  Get partner brand config
- useTranslation
  This hook returns the `t` function of the `i18next` library. For example,
  ```JavaScript
  const t = useTranslation()
  t("@1 day ago") // returns `1天前` when langugage is Simplified Chinese
  ```
- CIcon
  CIcon component will get icown SVG content from iconProvider by icon name and render to UI. For example, `<CIcon name="help" />` displays the question mark icon.
- CLocalTime
  Display local time text, it will render UTC time to the current agent's timezone and format. 
  For example:

    `<CLocalTime dateTime="2020-12-31T16:00Z" />` displays 
    `2021/01/01 00:00:00`

    when current agent timezone is `(UTC+08:00) Beijing, Chongqing, Hong Kong, Urumqi` and current agent date format is `YYYY/MM/DD HH:mm:ss`
- Access global settings in auto coding configuration: variable starts with `@` character
  - conditionForShowing: set a form component's `conditionForShowing` field to `@departmentConfig.isEnabled` to hide the component when the department is disabled.
  - text variable: you can have page title configured like this: `Current Agent Name: @currentAgent.displayName`.
