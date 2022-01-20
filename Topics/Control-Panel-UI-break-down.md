A typical page in the control panel is like the following:
![cpui.png](/.attachments/cpui-c4507531-5f44-4edb-82af-f2060fd2b134.png)

Control panel is a single-page application but the left part and right part are actually separanted Reactjs projects. In theory, it can even be a different version of Reactjs.
The left part belongs to ControlPanel (https://gitlab.comm100dev.io/x2/common/frontend/controlpanel) repository. 
The right part belongs to UIProject such as ControlPanelPage (https://gitlab.comm100dev.io/x2/common/frontend/controlpanelpage) repository.

## Page

There is only one browser page of the Control Panel application, the page here is "logical" page.

There are multiple "logical" pages in Control Panel. Different pages have different URLs. We split pages into different standalone UI projects and load/unload UI projects when the browser URL changes.

### URL breakdown

Control panel using React Router Library for page routing. React Router has a feature called `baseName`, which is convenient to set path prefix for all locations (https://v5.reactrouter.com/web/api/BrowserRouter/basename-string). This is why we can omit `siteId` in the link's `href`.

```
https://dash15.comm100.io
/ui/40100763/livechat/settings/autodistribution/
\__________/ \________________________________/
     |                        |         
  baseName (/ui/{siteId})    path

```

Meaning of different parts of a path:

```
https://dash15.comm100.io/ui/40100763/
livechat/settings/banlist/bannedvisitor/new
\______/ \______/ \_____/ \___________/ \_/ 
   |        |        │         │         │
level1menu  │        │         │        form (new form or edit form, optional)
(AKA module)│        │      entity(or tab)
            │  level2submenu(optional)
      level2menu(optional)
```



## Menu

There are three levels of menu:

![custom menu.png](/.attachments/custom%20menu-fa393ebd-ae73-44f0-b918-e7ba1d18b735.png)

You can config menu lable/icon etc in autocoding database. Related DB tables name are:
- dbo.t_autocoding_level1menu
- dbo.t_autocoding_level2menu
- dbo.t_autocoding_level2submenu

Document of menu configurations are here：[Menu](/References/UI/Menu)

