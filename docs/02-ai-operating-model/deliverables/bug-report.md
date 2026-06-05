# Bug Reports for automationexercise.com

## Bug 1
- **ID:** BUG_UI_001
- **Title:** HTTPS pages load insecure font resources and trigger mixed-content blocking
- **Module:** UI / Frontend
- **Severity:** High
- **Priority:** P1

- **Preconditions:**
  - Open `https://automationexercise.com/` or any secure page on the site.

## Steps to Reproduce
1. Navigate to `https://automationexercise.com/`.
2. Open the browser developer console.
3. Observe the network and console output.

- **Test Data:**
  - Browser: Chrome 114+ or any browser enforcing mixed-content blocking.

- **Expected Result:**
  - Page fonts and styles are loaded securely over HTTPS.
  - No mixed-content errors appear in the console.

- **Actual Result:**
  - The page requests font styles from `http://fonts.googleapis.com/...` over HTTP.
  - The browser blocks those requests, causing mixed-content errors.

- **Environment:**
  - URL / Instance: `https://automationexercise.com/`
- **Platform / OS:**
  - Windows 10 / macOS / Linux (browser-enforced behavior)
- **Browser / Device:**
  - Chrome-based browser

- **Logs / Console Output:**
  - `Mixed Content: The page at 'https://automationexercise.com/' was loaded over HTTPS, but requested an insecure stylesheet 'http://fonts.googleapis.com/css?family=Roboto:400,300,400italic,500,700,100'.`
  - Similar blocked requests for `Open+Sans` and `Abel` fonts.

- **Evidence to Provide:**
  1) Screenshot of the browser console showing mixed-content font requests.
  2) Network trace showing blocked HTTP font resources.

- **Regression Risk:**
  - Medium — visual rendering may degrade and user experience may be impacted, especially for secure builds.

- **Reported By:** [Name]
- **Date Reported:** [YYYY-MM-DD]
- **Assigned To:** [Developer/Team]
- **Status:** New

- **Comments / Workarounds:**
  - Use HTTPS URLs for Google Fonts or host fonts locally to eliminate mixed content.

## Bug 2
- **ID:** BUG_PERF_001
- **Title:** Product page loads blocked external resource due to CORS error
- **Module:** Performance / External integration
- **Severity:** Medium
- **Priority:** P2

- **Preconditions:**
  - Navigate to `https://automationexercise.com/products`.

## Steps to Reproduce
1. Open `https://automationexercise.com/products` in a browser.
2. Open the developer console.
3. Observe network and console errors related to external ad or consent services.

- **Test Data:**
  - Browser: Chrome-based browser

- **Expected Result:**
  - All external resources either load successfully or fail gracefully without console CORS errors.

- **Actual Result:**
  - The page logs a CORS error for `https://fundingchoicesmessages.google.com/...`.
  - The request is blocked due to missing `Access-Control-Allow-Origin` response header.

- **Environment:**
  - URL / Instance: `https://automationexercise.com/`
- **Platform / OS:**
  - Windows 10 / macOS / Linux
- **Browser / Device:**
  - Chrome-based browser

- **Logs / Console Output:**
  - `Access to XMLHttpRequest at 'https://fundingchoicesmessages.google.com/...' from origin 'https://automationexercise.com' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

- **Evidence to Provide:**
  1) Screenshot of the browser console showing the CORS error.
  2) Network request details for the blocked resource.

- **Regression Risk:**
  - Low to Medium — while the primary product flow may still work, user experience and page performance can be affected by failed external dependencies.

- **Reported By:** [Name]
- **Date Reported:** [YYYY-MM-DD]
- **Assigned To:** [Developer/Team]
- **Status:** New

- **Comments / Workarounds:**
  - Block or remove the failing external resource, or ensure the external service returns proper CORS headers.
