# Custom Component

Custom components allow you to customize only part of the page and leave everything else configured by auto coding. There are different locations (or slots) in a page that you can insert custom components:

- Form component: component in a form
- Form button: submit/cancel button
- Table button: New {entity name} button
- Table column: custom table cell
- Table filter: custom table data filters
- Table operation icon: icon button inside the operation column of a table
- Table batch operation button
- Area below a table
- Area below the page title
- Custom Preview Area
- Custom operator and value for rule condition editor

Document of custom component:
- [Custom Component](/References/Custom-Component)
- [Video, Live coding of creating custom component](https://comm100corp-my.sharepoint.com/:v:/g/personal/arihant_banthia_comm100_com/EUnqrL0WL7ZCkJiPlwPfLx8BU1Y57fm84XmAkKcFVopKiA)

# Free Style Page

There are cases that you need to do custom code for the whole page. For example, page like `Dashboard`, the UI doesn't relate to an entity.

The main logic of rendering different pages in the UI project is similar as follows:
```javascript
// persudo code
const pageType = getPageTypeByUIPageConfiguration(path)
if (pageType === "autoCodingPage") {
    // render CAutoCodingPage
} else if (pageType === "autoReportingPage") {
    // render CAutoReportingPage
} else if (pageType == "freeStylePage") {
   // use React route library's Route component to render UI base on path
}
```

