For special forms like “Import Intents”. we need create an entity with no corresponding database table and implement the backend API in custom code.
 
Create an entity named importChatbotIntent with two fields: mode and uploadTemplateFile. Create a form (NewEntityForm) for this entity and click import will send post request to /bot/chatbotintents:import. Below is [intents](https://dash11.comm100.io/ui/10100000/bot/aichatbot/intents/) page.

![specialform.png](/.attachments/specialform-bfa0737b-2bb0-4359-b522-d0053eb61981.png)

<details>
<summary>Example for special form</summary>

Below screenshot is a part of bot's [intents](https://dash11.comm100.io/ui/10100000/bot/aichatbot/intents/) page, click import button in left top of the page.

The configurations as following:
- entity
  - fields
    - uploadTemplateFile field
      - `name` is `uploadTemplateFile`
      - `type` is `file`
    - mode field
      - `name` is `uploadTemplateFile`
      - `type` is `file`
  - singleRowUI
    - `editFormName` is `''`
    - `newFormName` is `importChatbotIntent`
    - forms
      - importChatbotIntent form
        - `name` is `importChatbotIntent`
        - `title` is `Import Intents`
        - `description` is `Only text responses can be imported.`
        - `descriptionPosition` is `belowTitle`
        - `sizeForDisplayInDrawer` is `small`

</details>
