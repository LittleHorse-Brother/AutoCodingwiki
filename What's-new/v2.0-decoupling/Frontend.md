## General

  - Split front-end portal project into different UI projects (different git repositories)
  - Each UI project can be maintained/released separately
  - Each UI project can have different versions of the auto coding library and component library
  - Each page can be "routed" to a different UI project.
  - The menu part is not decoupled.

## Changes in Auto Coding Configuration

- Add table `t_AutoCoding_UIProject`. 
  - Name: nvarchar(256) primary key
  - CodeUrl: nvarchar(2048)
- The table `t_AutoCoding_UIPage` add fields:
  - ProjectName: nvarchar(256). Reference to `t_AutoCoding_UIProject`.

```note
  Note: Different tabs inside a page must be in the same project.
```

## About UIProject

Similar to the back-end project, each team can have its own ui projects

- All projects belong to the same domain, and the entire control panel is still a single page application
- Each project is released independently and can use different versions of the dependencies (framework, Autocoding, ReactJS, Material UI, etc.).
- Each project can use a different auto coding ER configuration or not use auto coding.
- Each project can run independently, so you can debug code during development.


## Implementation process

### Architecture

- The architecture team will split the current Control Panel
  - Divide the current ControlPanel project into ControlPanel and ControlPanelPage projects.
  - Add a record in `t_AutoCoding_UIProject`

    | Name | CodeUrl |
    | - | - |
    | ControlPanelPage | /frontend/ControlPanelPage/index.js |
  - Update the all `ProjectName` of `UIPage` to `ControlPanelPage`

### Project Team

- Global team needs to change the login application, redirect to a full path after login (right now, it jumps to `/ui/{siteId}/` after login, which is not enough to identify the UI project).
- need to create a UI project based on the ControlPanelPage repo
    - remove other project's code (custom components mainly) in ControlPanelPage
    - load current project's entities configuration at `main` function.
- need to create UI project record in `t_AutoCoding_UIProject`

### Project division

Because front-end projects depend on the back-end's entities configuration, it is recommended that the front-end projects be split according to the back-end's service.
- `livechat`
- `livechathistory`
- `bot`
- `ticketing`
- `global`
