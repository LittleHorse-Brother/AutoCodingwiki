The following are steps of startup process:
1. Download html/js code.
1. Download `pages` configurations and initialize UI project by calling the `main` function of UI project. In the meantime, also downloads the code and configurations for the left side menu.
1. UI project fetches `site` object, `entities` configurations as well as other data and renders the page UI.


## Download html/js code
   Any path matches `/ui/**` will return the `index.html` file in the `ControlPanel` repository. `index.html` call the `main` function of `ControlPanel`. `main` function located in `index.tsx` file in `ControlPanel` repositiory.

## "Route" to a UI Project
1. Get all pages from this address: https://dash15.comm100.io/entityapi/pages
  Each page contains a `project` field with `codeUrl` field in it.
  ```json
    {
      //... other fields ...
      "path": "/livechat/dashboard/",
      "project": {
          "name": "ControlPanelPage",
          "codeUrl": "/frontend/ControlPanelPage/index.js"
      }
   }
  ```
  `codeUrl` is the entry point of the `ControlPanelPage` UI project.

2. Find `page` object by browser path, in our case, path is `/livechat/dashboard/` (Note: path doesn't include `/ui/{siteId}` part)

3. Download `codeUrl` and execute by creating a `script` tag with `src` equal to `codeUrl`.
  ```javascript
// persudo code:
if (!document.querySelector(`script[data-project=${page.project.name}]`)) {
    unloadCurrentProject();

    const script = document.createElement('script');
    script.src = page.project.codeUrl;
    script.type = "text/javascript";
    script.setAttribute("data-project", page.project.name);
    document.head.appendChild(script);
}
  ```
4. The UI project calls the` window.registerProject` method to register the project's main function.

```javascript
window.registerProject({
    name: "ControlPanelPage",
    // entry method of UI project, persudo code:
    main: () => {
        // install axios middleware for refreshing token
        const cancelRefreshToken = refreshToken(serverUrlPrefix);
        // install axios middleware for the global network loading indicator progress bar (display loading if there are network activities)
        const cancelMonitor = monitorNetwork(serverUrlPrefix);
        const container = document.createElement("div");
        // add div to DOM tree
        ReactDOM.render(React.createElement(CMain, {}), container);
        // return unload function for clearup when switch to another UI project.
        return () => {
            ReactDOM.unmountComponentAtNode(container);
            container.remove();
            cancelMonitor();
            cancelRefreshToken();
        }
    },
});
```
Note: `main` function MUST NOT be async (must be atomic), otherwise it might get race condition when switching between different UI projects quickly.

5. Control panel call `main` function of UI project.

## UI project startup process

1. After calling `main` function of a UI project, it starts to download configurations for the page.

```javascript
// initialize.ts
export const initialize = async (flags: Flags) => {
  // configs contains url prefix of api and other configurations etc.
  const configs = await getConfigs(flags);
  // site object contains site configurations such as `features` of a site.
  const site = await getSiteInfo(configs.authServiceUrlPrefix as string);
  // currentAgent contains logined agent name/avatar/permissions etc.
  const currentAgent = await getCurrentAgent(configs.serverUrlPrefix as string);
  // entities contains autocoding configurations, parameter ["key"] here means only download knowledgebase related entities.
  const entities = await new EntityInfoDomainService({
    urlPrefix: configs.serverUrlPrefix,
  }).get(["kb"]);

  // return global settings
}
```
Note: Details about global settings are described here: [/Topics/Front-End-Global-Settings](/Topics/Front-End-Global-Settings)

2. Render page

   There are 3 kinds of pages: （`CRoot.tsx` file)
   - auto coding page
     Provide custom components by `ExtensionProvider` react context
   - auto reporting page (optional, some UI projects doesn't have report pages)
   - freestyle page (optional, some UI projects doesn't have freestyle pages)

