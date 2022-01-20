# Control Panel

The Control panel consists of many modules (product lines), the following are shared repositories.

- Control Panel: https://gitlab.comm100dev.io/x2/common/frontend/controlpanel
  This is the entrance of the Control Panel, it is a React application. It contains menu UI and loads `UIProject` base on browser URL.
   - Menu library: https://gitlab.comm100dev.io/x2/common/custommenu
     Contains the menu component.

![cpui.png](/.attachments/cpui-eca6877f-9254-4d1c-9965-4e6a0993c850.png)

We split different control panel pages into different react apps, AKA `UIProject`, right now most of the pages are in the `ControlPanelPage` UI project.

- Control Panel Page: https://gitlab.comm100dev.io/x2/common/controlpanelpage
  This is a React application. This is the main `UIProject` of the control panel website, it will be split into different UIProject in the future.
- Knowledgebase: https://gitlab.comm100dev.io/x2/livechat/frontend/knowledgebase
  This is a React application. This is a `UIProject` which covers the knowledgebase module's pages.
  Note: Knowledgebase is not a shared repository. I put it here to emphasize that there are multiple UI projects.


Applications above depend on the following libraries:
These libraries are published to the private npm server, you can install them by the `npm install @comm100/xxx` command.
- @comm100/framework: https://gitlab.comm100dev.io/x2/common/frontend/framework
  Shared components and API access infrastructure etc.
- @comm100/styledComponents: https://gitlab.comm100dev.io/x2/common/frontend/styledComponents
  CSS of shared components
- @comm100/autocoding: https://gitlab.comm100dev.io/x2/architect/frontend/autocoding
  Render pages by auto coding configurations.
- @comm100/autoreporting: https://gitlab.comm100dev.io/x2/architect/frontend/autoreporting: Render pages by auto reporting configurations
- @comm100/test: https://gitlab.comm100dev.io/x2/architect/frontend/e2etest: e2etest helpers.

Summarize

| Repo | Gitlab path | Type |
|--|--|--|--|
| ControlPanel | /x2/common/frontend/controlpanel | App |
| CustomMenu | /x2/common/custommenu | Library | @comm100/custommenu |
| ControlPanelPage | /x2/common/controlpanelpage | UI Project |
| Knowledgebase | /x2/livechat/frontend/knowledgebase | UI Project |
| Framework | /x2/common/framework | Library | @comm100/framework |
| StyledComponents | /x2/common/styledComponents | Library |
| AutoCoding | /x2/architect/frontend/autocoding | Library |
| AutoReporting | /x2/architect/frontend/autoreporting | Library |
| E2ETest | /x2/architect/frontend/e2etest | Library |


# Agent Console
- Live chat part: https://gitlab.comm100dev.io/x2/livechat/frontend
- Ticketing & Messaging: https://gitlab.comm100dev.io/x2/ticket/frontend

# Visitor Side
- https://gitlab.comm100dev.io/x2/livechat/frontend