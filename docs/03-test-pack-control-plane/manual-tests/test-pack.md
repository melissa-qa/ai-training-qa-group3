# Test Pack: AE-1 User Registration

Source: [UserStories](docs/03-test-pack-control-plane/UserStories.md) — Story AE-1
Traceability: `Requirements v1.md` (User Management: registration, duplicate-email validation)

---

## TC-AE1-001
- **Title:** New user registration with unique email succeeds
- **Module:** User Management / Registration
- **Tags:** registration, positive, sanity
- **Priority:** P0 (Critical)
- **Gate:** PR / Nightly
- **Traceability:** AE-1 acceptance criteria 2–4; Requirements v1.md: User Management (registration)

- **Preconditions:**
  - Test environment available (QA/staging).
  - No account exists for test email `qa.tester+<timestamp>@example.com`.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. On the `Signup / Login` page, enter `QA Tester` in the Name field.
2. Enter a unique email `qa.tester+<timestamp>@example.com` in the Email Address field.
3. Click the `Signup` button.
4. Complete any additional registration fields shown (password, DOB, address) and submit.
5. Observe the resulting page/confirmation.

- **Test Data:**
  - Name: QA Tester
  - Email: qa.tester+20260602_001@example.com
  - Password: Test@1234
  - Address: 123 Test St, Test City

- **Expected Result:**
  - Account is created successfully and user sees confirmation (e.g., `ACCOUNT CREATED!`).
  - User can proceed to login or is automatically logged in per UX.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of success message, API response or confirmation page link
- **Notes:** After test, optionally delete or record created account for cleanup.

---

## TC-AE1-002
- **Title:** Duplicate email registration attempt is rejected
- **Module:** User Management / Registration
- **Tags:** registration, negative, duplicate
- **Priority:** P0 (Critical)
- **Gate:** PR / Nightly
- **Traceability:** AE-1 acceptance criteria 2; Requirements v1.md: prevent duplicate email registrations

- **Preconditions:**
  - An existing account with email `existing.user@example.com` exists in the test environment.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. On the `Signup / Login` page, enter `Existing User` in Name.
2. Enter the existing email `existing.user@example.com` in Email Address.
3. Click `Signup` and complete any required fields.
4. Submit the registration form.

- **Test Data:**
  - Name: Existing User
  - Email: existing.user@example.com

- **Expected Result:**
  - Registration is rejected with a clear error message indicating the email is already registered.
  - No new account is created and HTTP/API call returns appropriate validation error (e.g., 409/validation message).

- **Actual Result:**
  - 

- **Execution Status:**
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of error message; server/API response if available
- **Notes:** If environment does not provide pre-seeded account, create one first and record cleanup steps.

---

## TC-AE1-003
- **Title:** Form validation — incomplete fields block submission
- **Module:** User Management / Registration
- **Tags:** validation, negative, client-side
- **Priority:** P1 (High)
- **Gate:** PR
- **Traceability:** AE-1 acceptance criteria 2–3; Requirements v1.md: input validation

- **Preconditions:**
  - Tester on `Signup / Login` page.

## Steps to Reproduce
1. Enter `QA Tester` in Name, leave Email blank (or vice versa).
2. Click `Signup` or submit registration.
3. Observe form behavior and validation messages.

- **Test Data:**
  - Name: QA Tester
  - Email: (blank)

- **Expected Result:**
  - The form prevents submission and displays inline validation messages for required fields.
  - No API call for registration is made when client-side validation prevents submission.

- **Actual Result:**
  - 

- **Execution Status:**
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of validation messages; network trace showing no registration submission
- **Notes:** Repeat for other required fields (password, mandatory profile fields).

---

## TC-AE1-004
- **Title:** Success message 'ACCOUNT CREATED!' displays after valid registration
- **Module:** User Management / Registration
- **Tags:** registration, feedback, UI
- **Priority:** P1 (High)
- **Gate:** PR / Nightly
- **Traceability:** AE-1 acceptance criteria 4; Requirements v1.md: user feedback messages

- **Preconditions:**
  - Unique email available.
  - Tester on `Signup / Login` page.

## Steps to Reproduce
1. Complete registration with valid details using a unique email.
2. Submit the form and wait for confirmation.
3. Observe and capture the confirmation message area.

- **Test Data:**
  - Name: QA Confirm
  - Email: qa.confirm+20260602_001@example.com

- **Expected Result:**
  - A visible success message `ACCOUNT CREATED!` appears and is accessible (screen reader readable).
  - Message includes next action instructions (e.g., proceed to login).

- **Actual Result:**
  - 

- **Execution Status:**
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of `ACCOUNT CREATED!` message
- **Notes:** Verify accessibility of message (aria-live or focus behavior) if applicable.

---

## TC-AE1-005
- **Title:** Navigation to Signup/Login page via header link
- **Module:** Navigation / Header
- **Tags:** navigation, smoke, header
- **Priority:** P2 (Medium)
- **Gate:** PR (Smoke)
- **Traceability:** AE-1 acceptance criteria 1; Requirements v1.md: persistent header navigation

- **Preconditions:**
  - Tester on homepage `https://automationexercise.com/`.

## Steps to Reproduce
1. From the page header, click the `Signup / Login` link.
2. Verify the browser navigates to `/login` and page heading shows `Login to your account` or equivalent.

- **Test Data:** n/a

- **Expected Result:**
  - The `Signup / Login` header link directs to the login/signup page within one navigation step.
  - No broken links or 404 encountered.

- **Actual Result:**
  - 

- **Execution Status:**
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of header and resulting login page URL
- **Notes:** Include link integrity check for header across key pages.

---

## TC-AE1-006
- **Title:** Email field validation rejects invalid formats
- **Module:** User Management / Registration
- **Tags:** validation, negative, input
- **Priority:** P1 (High)
- **Gate:** PR
- **Traceability:** AE-1 acceptance criteria 2; Requirements v1.md: input validation

- **Preconditions:**
  - Tester on `Signup / Login` page.

## Steps to Reproduce
1. Enter `QA Tester` in Name and an invalid email `invalid-email` in Email Address.
2. Click `Signup` and attempt to submit the registration form.

- **Test Data:**
  - Name: QA Tester
  - Email: invalid-email

- **Expected Result:**
  - The form shows a validation error for invalid email format and blocks submission.
  - If server-side validation occurs, response includes appropriate validation error code/message.

- **Actual Result:**
  - 

- **Execution Status:**
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of validation message; network/server response if applicable
- **Notes:** Test other invalid formats (missing @, missing domain) as subcases.

---

## TC-AE1-007
- **Title:** Registered user can log in immediately after account creation
- **Module:** User Management / Login
- **Tags:** registration, login, integration
- **Priority:** P0 (Critical)
- **Gate:** Nightly
- **Traceability:** AE-1 acceptance criteria 4; Requirements v1.md: user persistence and login

- **Preconditions:**
  - Complete registration via AE1-001 or have an active newly-created account.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. After successful registration, navigate to login page (or use provided flow if auto-logged-in).
2. Enter newly-created email and password.
3. Click `Login` and observe the post-login state.

- **Test Data:**
  - Email/password from successful AE1-001 run.

- **Expected Result:**
  - User is able to log in immediately; UI shows logged-in state (`Logged in as [username]`).
  - No delay or replication issue prevents immediate login.

- **Actual Result:**
  - 

- **Execution Status:**
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of `Logged in as [username]` and session cookie/network login response
- **Notes:** If login fails right after registration, capture server logs and timestamps for triage.

---

## TC-AE2-001
- **Title:** Login with valid credentials succeeds
- **Module:** User Management / Login
- **Tags:** login, positive, sanity
- **Priority:** P0 (Critical)
- **Gate:** PR / Nightly
- **Traceability:** AE-2 acceptance criteria 1–3; Requirements v1.md: User Management (login)

- **Preconditions:**
  - Valid registered user exists.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. Enter valid email and password.
2. Click `Login`.
3. Observe the page for logged-in state.

- **Test Data:**
  - Email: registered.user@example.com
  - Password: Test@1234

- **Expected Result:**
  - User is successfully logged in.
  - Page displays `Logged in as [username]` or equivalent.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of successful logged-in state
- **Notes:** Validate that the session is established for later navigation.

---

## TC-AE2-002
- **Title:** Invalid password shows clear rejection message
- **Module:** User Management / Login
- **Tags:** login, negative, validation
- **Priority:** P1 (High)
- **Gate:** PR
- **Traceability:** AE-2 acceptance criteria 1–3; Requirements v1.md: User Management (login validation)

- **Preconditions:**
  - Valid registered user exists.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. Enter valid email and incorrect password.
2. Click `Login`.
3. Observe the error message.

- **Test Data:**
  - Email: registered.user@example.com
  - Password: WrongPass1

- **Expected Result:**
  - Login is rejected with a visible error message indicating invalid credentials.
  - User remains on the login page.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of invalid credentials message
- **Notes:** Confirm the error does not reveal sensitive information.

---

## TC-AE2-003
- **Title:** Locked or disabled account returns appropriate error
- **Module:** User Management / Login
- **Tags:** login, negative, security
- **Priority:** P1 (High)
- **Gate:** Nightly
- **Traceability:** AE-2 acceptance criteria 1–3; Requirements v1.md: User Management (account integrity)

- **Preconditions:**
  - A disabled or locked user account exists in the test environment.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. Enter the disabled user email and password.
2. Click `Login`.
3. Observe the error feedback.

- **Test Data:**
  - Email: disabled.user@example.com
  - Password: Test@1234

- **Expected Result:**
  - Login is blocked and the user receives a message indicating account status.
  - The site does not proceed to the logged-in area.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of locked/disabled account error
- **Notes:** Create or seed test account if needed before execution.

---

## TC-AE2-004
- **Title:** Session created after login persists across navigation
- **Module:** User Management / Session
- **Tags:** login, session, persistence
- **Priority:** P1 (High)
- **Gate:** Nightly
- **Traceability:** AE-2 acceptance criteria 1–3; Requirements v1.md: User Management and session persistence

- **Preconditions:**
  - Valid registered user exists.
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. Log in with valid user credentials.
2. Navigate to a different page via the site header.
3. Confirm user remains logged in.

- **Test Data:**
  - Email: registered.user@example.com
  - Password: Test@1234

- **Expected Result:**
  - Logged-in state persists across internal navigation.
  - User is not asked to log in again on page change.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of logged-in UI after navigation
- **Notes:** Check cookie/session storage behavior if available.

---

## TC-AE2-005
- **Title:** Login form resists injection or malformed input
- **Module:** User Management / Login
- **Tags:** security, validation
- **Priority:** P1 (High)
- **Gate:** PR
- **Traceability:** AE-2 acceptance criteria 1–3; Requirements v1.md: Input validation and security

- **Preconditions:**
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. Enter malicious input such as `'; DROP TABLE users; --` into the email field.
2. Enter a normal password.
3. Click `Login`.
4. Observe any validation or error response.

- **Test Data:**
  - Email: `'; DROP TABLE users; --`
  - Password: Test@1234

- **Expected Result:**
  - The login form rejects malformed input and displays a safe error message.
  - No unexpected behavior or database errors are exposed.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of validation feedback or site behavior
- **Notes:** Do not use destructive payloads; focus on input sanitization behavior.

---

## TC-AE2-006
- **Title:** Login form operable via keyboard and screen readers
- **Module:** User Management / Accessibility
- **Tags:** accessibility, keyboard, login
- **Priority:** P2 (Medium)
- **Gate:** PR
- **Traceability:** AE-2 acceptance criteria 1–3; Requirements v1.md: Accessibility (keyboard navigation, labels)

- **Preconditions:**
  - Tester on `https://automationexercise.com/login`.

## Steps to Reproduce
1. Tab through the login form fields.
2. Enter valid credentials using keyboard only.
3. Press Enter to submit.
4. Verify the form is announced correctly by a screen reader.

- **Test Data:**
  - Email: registered.user@example.com
  - Password: Test@1234

- **Expected Result:**
  - The login form can be completed and submitted entirely via keyboard.
  - Screen-reader accessible labels are present.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Notes on keyboard flow and accessibility findings
- **Notes:** Verify focus order and label associations.

---

## TC-AE3-001
- **Title:** Logout ends session and redirects to login page
- **Module:** User Management / Logout
- **Tags:** logout, session, security
- **Priority:** P0 (Critical)
- **Gate:** PR / Nightly
- **Traceability:** AE-3 acceptance criteria 1–2; Requirements v1.md: User Management (session termination)

- **Preconditions:**
  - User is logged in.
  - Tester on any authenticated page.

## Steps to Reproduce
1. Click the `Logout` button.
2. Observe redirection to the login page.
3. Confirm the user is no longer logged in.

- **Test Data:**
  - Valid logged-in session

- **Expected Result:**
  - The user is redirected to the login page.
  - Logged-in indicators are removed.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of login page after logout
- **Notes:** Verify logout is effective across the site.

---

## TC-AE3-002
- **Title:** Protected pages are inaccessible after logout
- **Module:** User Management / Access Control
- **Tags:** logout, access control, security
- **Priority:** P1 (High)
- **Gate:** Nightly / Release
- **Traceability:** AE-3 acceptance criteria 1–2; Requirements v1.md: User Management (session persistence)

- **Preconditions:**
  - User is logged in.
  - User has access to a protected page such as account details.

## Steps to Reproduce
1. Log out from the application.
2. Attempt to navigate back to a protected page.
3. Observe whether access is denied.

- **Test Data:**
  - Protected page URL, e.g., account dashboard or order history

- **Expected Result:**
  - The site redirects to login or denies access without showing protected content.
  - Protected resources are not accessible after logout.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of login redirect or access denied state
- **Notes:** Check browser back-button behavior too.

---

## TC-AE3-003
- **Title:** Header Logout link works from any page (smoke)
- **Module:** Navigation / Logout
- **Tags:** logout, navigation, smoke
- **Priority:** P2 (Medium)
- **Gate:** PR (Smoke)
- **Traceability:** AE-3 acceptance criteria 1; Requirements v1.md: persistent header navigation

- **Preconditions:**
  - User is logged in.
  - Tester on a non-login authenticated page.

## Steps to Reproduce
1. Click the `Logout` link in the header.
2. Verify the user is logged out.
3. Verify return to login page.

- **Test Data:**
  - Valid logged-in session

- **Expected Result:**
  - Header logout link immediately logs out the user and returns to login.
  - No broken link or navigation failure occurs.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of logout flow
- **Notes:** Test from both home and product pages if possible.

---

## TC-AE3-004
- **Title:** Logout clears sensitive cookies/local storage values
- **Module:** User Management / Security
- **Tags:** logout, security, data
- **Priority:** P1 (High)
- **Gate:** Nightly
- **Traceability:** AE-3 acceptance criteria 1–2; Requirements v1.md: User Management (security)

- **Preconditions:**
  - User is logged in.
  - Browser developer tools or instrumentation available.

## Steps to Reproduce
1. Log in with valid credentials.
2. Note authentication cookies/local storage values.
3. Log out.
4. Confirm session-related storage is cleared.

- **Test Data:**
  - Logged-in user session

- **Expected Result:**
  - Session cookies and local storage related to authentication are removed.
  - No sensitive values remain after logout.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Notes/screenshots of browser storage before and after logout
- **Notes:** Focus on auth/session keys, not unrelated site preferences.

---

## TC-AE3-005
- **Title:** Logout action operable via keyboard and announced to assistive tech
- **Module:** User Management / Accessibility
- **Tags:** accessibility, logout, keyboard
- **Priority:** P2 (Medium)
- **Gate:** PR
- **Traceability:** AE-3 acceptance criteria 1–2; Requirements v1.md: Accessibility (keyboard navigation)

- **Preconditions:**
  - User is logged in.
  - Tester on a page with the logout link.

## Steps to Reproduce
1. Navigate to the logout link using the keyboard.
2. Activate the link using Enter or Space.
3. Observe page transition and any assistive announcement.

- **Test Data:**
  - Logged-in user session

- **Expected Result:**
  - Logout is triggered via keyboard.
  - The action is announced or otherwise accessible.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Notes on keyboard flow and accessibility behavior
- **Notes:** Validate focus order and visual indicator on selection.

---

## TC-AE4-001
- **Title:** Exact-match search returns relevant products
- **Module:** Product Search
- **Tags:** search, positive, functional
- **Priority:** P0 (Critical)
- **Gate:** PR / Nightly
- **Traceability:** AE-4 acceptance criteria 1–3; Requirements v1.md: Product Catalog (search)

- **Preconditions:**
  - Tester on `https://automationexercise.com/products`.
  - Searchable products exist.

## Steps to Reproduce
1. Enter an exact product name into the search bar.
2. Click the search icon.
3. Verify the search results.

- **Test Data:**
  - Search term: Blue Top

- **Expected Result:**
  - Search results include products that exactly match the search term.
  - Results list is relevant to the query.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of search results page
- **Notes:** Confirm the product is visible and matches the query.

---

## TC-AE4-002
- **Title:** Partial and case-insensitive searches return expected results
- **Module:** Product Search
- **Tags:** search, robustness
- **Priority:** P1 (High)
- **Gate:** Nightly
- **Traceability:** AE-4 acceptance criteria 1–3; Requirements v1.md: Product Catalog (search)

- **Preconditions:**
  - Tester on product search page.

## Steps to Reproduce
1. Enter a partial product keyword such as `blue`.
2. Click the search icon.
3. Verify results include matching products regardless of case.

- **Test Data:**
  - Search term: blue

- **Expected Result:**
  - Results include products with matching keywords in any case.
  - Search is not strictly case-sensitive.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of matching results
- **Notes:** Use both upper and lower case terms if possible.

---

## TC-AE4-003
- **Title:** No-results search displays helpful UX message
- **Module:** Product Search
- **Tags:** search, UX, negative
- **Priority:** P1 (High)
- **Gate:** PR
- **Traceability:** AE-4 acceptance criteria 1–3; Requirements v1.md: Product Catalog (search)

- **Preconditions:**
  - Tester on product search page.

## Steps to Reproduce
1. Enter a search term that does not match any products.
2. Click the search icon.
3. Observe the no-results behavior.

- **Test Data:**
  - Search term: NonexistentProduct123

- **Expected Result:**
  - The site displays a clear no-results message.
  - The user is guided to try another search or browse categories.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of no-results message
- **Notes:** Confirm the message is user-friendly and visible.

---

## TC-AE4-004
- **Title:** Search returns results within performance thresholds
- **Module:** Product Search / Performance
- **Tags:** search, performance
- **Priority:** P1 (High)
- **Gate:** Release
- **Traceability:** AE-4 acceptance criteria 1–3; Requirements v1.md: Performance (API latency)

- **Preconditions:**
  - Tester on product search page.
  - Test environment stable.

## Steps to Reproduce
1. Enter a valid product search term.
2. Click the search icon.
3. Measure result response time.

- **Test Data:**
  - Search term: Blue Top

- **Expected Result:**
  - Search results load correctly.
  - Response time is within acceptable threshold (<200ms for API or under 2 seconds for UI load).

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Timing measurement notes and screenshot
- **Notes:** Capture the metric tool or browser timing if possible.

---

## TC-AE4-005
- **Title:** Search input safely handles special characters and prevents injection
- **Module:** Product Search / Security
- **Tags:** security, validation
- **Priority:** P1 (High)
- **Gate:** PR
- **Traceability:** AE-4 acceptance criteria 1–3; Requirements v1.md: Input validation

- **Preconditions:**
  - Tester on product search page.

## Steps to Reproduce
1. Enter a special-character search term such as `'; DROP TABLE products; --`.
2. Click the search icon.
3. Observe behavior and any error messages.

- **Test Data:**
  - Search term: `'; DROP TABLE products; --`

- **Expected Result:**
  - The search is rejected or safely handled.
  - No injection or server error occurs.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of safe error handling or empty result set
- **Notes:** This is a security-focused validation.

---

## TC-AE4-006
- **Title:** Real-time search or suggestions behave correctly across responsive breakpoints
- **Module:** Product Search / Responsive UI
- **Tags:** search, responsive, accessibility
- **Priority:** P2 (Medium)
- **Gate:** Nightly
- **Traceability:** AE-4 acceptance criteria 1–3; Requirements v1.md: Responsive design

- **Preconditions:**
  - Tester on product search page.
  - Browser viewport set to Desktop, Tablet, Mobile breakpoints.

## Steps to Reproduce
1. Enter a search term on Desktop viewport.
2. Observe search suggestions or results display behavior.
3. Repeat on Tablet and Mobile viewport widths.

- **Test Data:**
  - Search term: Blue

- **Expected Result:**
  - Search behavior remains functional and visible across breakpoints.
  - Suggestions or results are accessible and not clipped.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshots of results in different viewports
- **Notes:** Note any layout breakage on smaller screens.

---

## TC-AE5-001
- **Title:** Add single product updates cart count and total correctly
- **Module:** Shopping Cart / Add to Cart
- **Tags:** cart, pricing, positive
- **Priority:** P0 (Critical)
- **Gate:** PR / Nightly
- **Traceability:** AE-5 acceptance criteria 1–3; Requirements v1.md: Shopping Cart (add/remove, totals)

- **Preconditions:**
  - Tester on `https://automationexercise.com/products`.
  - At least one product is visible.

## Steps to Reproduce
1. Click `Add to cart` on a product.
2. Navigate to the cart page.
3. Verify cart count and total price.

- **Test Data:**
  - Product: Blue Top
  - Expected price: Rs. 500

- **Expected Result:**
  - Product is added to cart.
  - Cart count increments and total reflects item price.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of cart contents and totals
- **Notes:** Verify the product label and price are correct.

---

## TC-AE5-002
- **Title:** Add multiple distinct products shows correct line items and totals
- **Module:** Shopping Cart / Add to Cart
- **Tags:** cart, regression, totals
- **Priority:** P1 (High)
- **Gate:** Nightly
- **Traceability:** AE-5 acceptance criteria 1–3; Requirements v1.md: Shopping Cart (totals)

- **Preconditions:**
  - Tester on product listing page.
  - Multiple products available.

## Steps to Reproduce
1. Add two different products to the cart.
2. Navigate to the cart page.
3. Verify two line items appear with correct individual prices and combined total.

- **Test Data:**
  - Product 1: Blue Top (Rs. 500)
  - Product 2: Men Tshirt (Rs. 400)

- **Expected Result:**
  - Both products appear in the cart.
  - The total equals the sum of both prices.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of cart with both items and total
- **Notes:** Ensure quantity remains 1 for each item.

---

## TC-AE5-003
- **Title:** Adding same product increments quantity and updates totals correctly
- **Module:** Shopping Cart / Quantity
- **Tags:** cart, quantity, totals
- **Priority:** P1 (High)
- **Gate:** Nightly
- **Traceability:** AE-5 acceptance criteria 1–3; Requirements v1.md: Shopping Cart (quantity)

- **Preconditions:**
  - Tester on product listing or detail page.
  - Product available to add.

## Steps to Reproduce
1. Add the same product to cart twice.
2. Navigate to the cart page.
3. Verify the product quantity increments to 2 and total updates.

- **Test Data:**
  - Product: Blue Top
  - Unit price: Rs. 500

- **Expected Result:**
  - Quantity shows 2 for the product.
  - Total equals 2 × unit price.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of cart quantity and total calculation
- **Notes:** Confirm that duplicate line items are not shown separately.

---

## TC-AE5-004
- **Title:** Add-to-cart from Recommended Items adds item to cart correctly
- **Module:** Shopping Cart / Recommended Items
- **Tags:** cart, recommendation, integration
- **Priority:** P2 (Medium)
- **Gate:** PR
- **Traceability:** AE-5 acceptance criteria 1–3; Requirements v1.md: Shopping Cart (add to cart)

- **Preconditions:**
  - Tester on the homepage with recommended items visible.

## Steps to Reproduce
1. Scroll to the Recommended Items section.
2. Click `Add to cart` on a recommended product.
3. Navigate to the cart page.
4. Verify the recommended item is present.

- **Test Data:**
  - Recommended product: visible on homepage

- **Expected Result:**
  - Product is added to cart successfully.
  - Cart shows the recommended item and correct price.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of cart showing recommended item
- **Notes:** Confirm recommended item behavior is consistent.

---

## TC-AE5-005
- **Title:** Cart preserves items across navigation and logged-in sessions
- **Module:** Shopping Cart / Session
- **Tags:** cart, persistence, session
- **Priority:** P1 (High)
- **Gate:** Nightly / Release
- **Traceability:** AE-5 acceptance criteria 1–3; Requirements v1.md: Shopping Cart (persistence)

- **Preconditions:**
  - User is logged in or has an active cart session.
  - Cart contains at least one item.

## Steps to Reproduce
1. Add a product to the cart.
2. Navigate to another page.
3. Return to the cart and verify the item remains.
4. Optional: log out and log in again, then verify cart contents if session persistence is expected.

- **Test Data:**
  - Product: Blue Top

- **Expected Result:**
  - Cart item remains after navigation.
  - When in a logged-in session, cart contents persist across page loads.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of cart after navigation
- **Notes:** Note any session timeout or loss of cart contents.

---

## TC-AE5-006
- **Title:** Add-to-cart confirmation modal is shown and accessible
- **Module:** Shopping Cart / Accessibility
- **Tags:** cart, accessibility, feedback
- **Priority:** P2 (Medium)
- **Gate:** PR
- **Traceability:** AE-5 acceptance criteria 1–3; Requirements v1.md: User feedback and accessibility

- **Preconditions:**
  - Tester on product listing or homepage.

## Steps to Reproduce
1. Click `Add to cart` on a product.
2. Observe the confirmation modal or message.
3. Verify it is visible and keyboard accessible.

- **Test Data:**
  - Product: Blue Top

- **Expected Result:**
  - Confirmation appears after adding to cart.
  - The modal/message can be dismissed and is keyboard accessible.

- **Actual Result:**
  - 

- **Execution Status:** Pass / Fail / Blocked / Not Executed
- **Executed By:**
- **Execution Date:**
- **Evidence:** Screenshot of add-to-cart confirmation
- **Notes:** Verify that assistive text or ARIA attributes are present.
