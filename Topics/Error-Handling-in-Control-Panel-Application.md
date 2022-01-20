There are the following types of errors in the Control Panel:

- Toast error
  - Network error
  - Back end API error: non-2xx status code

- 401 Error
  Jump to the login page when 401 error occurred

- Page Crash
  - 404: path not found in `dbo.t_autocoding_uipage` table
  - WAF error
  - Exception during the startup process
     - API failed
     - Miss-configuration in auto coding database
     - etc.
  - Render exception which catched by the root error boundary


## Implementation

Listen `unhandledrejection` globally and do different operations depending on the error context. For example, if it is a network request (axios request) and if the response status code is 401, then redirect to the login page. This part of logic is in `ControlPanel` repository's `MainApp.ts` file.

We also use React library's `ErrorBoundary` to catch exceptions during the rendering process. Render the `CCrashPage` component when there is an exception. This code is also in the `ControlPanel` repository.



