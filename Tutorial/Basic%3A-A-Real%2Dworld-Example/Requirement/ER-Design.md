Usually, it is the product team's job to provide ER Design. Here is a document you might receive from the product team:
https://comm100corp.sharepoint.com/:w:/s/Comm100/ESdfGrbzYuVHrKhTr-SLNbYBG1NYeQmAyhi1KWPuQKr5LQ?e=RrLYxR

In this tutorial the ER is very simple, there is only one entity: blocked sender.

##Entity

**Name**: `BlockedSender`
**Is multiple records**: `yes` (Customers can create multiple blocked senders in a Comm100 site)

### Fields
- Id: `GUID` of current record
- SiteId: Comm100 site id
- EmailOrDomain: `Required` `string`
- BlockLevel: `enum`: `markFutureMessagesAsJunk (default)` `rejectAllFutureMessages`
