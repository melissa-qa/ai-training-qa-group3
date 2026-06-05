# Test Cases for automationexercise.com

## Test Case 1
- **ID:** TC_USER_001
- **Title:** User registration with unique email succeeds
- **Module:** User Management
- **Priority:** High
- **Preconditions:**
  - User is on `https://automationexercise.com/login`.
  - No existing account exists for the test email.

## Steps to Reproduce
1. Enter a valid name in the Name field.
2. Enter a unique email address in the Email Address field.
3. Click the `Signup` button.
4. Complete any required registration form fields if prompted.
5. Submit the registration form.

- **Test Data:**
  - Name: `QA Tester`
  - Email: `qa.tester+unique@example.com`
  - Password: `Test@1234` (if prompted)
  - Country / address values: valid dummy values if required.

- **Expected Result:**
  - User account is created successfully.
  - A confirmation message appears and the user is able to proceed to login or account dashboard.

- **Actual Result:**
  - [To be filled during execution]

- **Execution Status:**
  - Pass / Fail / Blocked / Not Executed

- **Executed By:** [Name]
- **Execution Date:** [YYYY-MM-DD]
- **Evidence:**
  - Screenshot of account creation success.
  - Registration confirmation message or account dashboard.

- **Notes:**
  - Verify duplicate email rejection in a separate negative test case.

## Test Case 2
- **ID:** TC_CART_001
- **Title:** Add product to cart and verify cart totals
- **Module:** Shopping Cart
- **Priority:** High
- **Preconditions:**
  - User is on `https://automationexercise.com/products`.
  - At least one product is visible in the product catalog.

## Steps to Reproduce
1. Select a visible product from the catalog (for example, `Blue Top`).
2. Click the `Add to cart` button for the selected product.
3. Navigate to the `Cart` page via the header link.
4. Verify the product appears in the cart with the correct name, unit price, and quantity.
5. Confirm the cart total reflects the item price and quantity correctly.

- **Test Data:**
  - Product: `Blue Top`
  - Expected unit price: `Rs. 500`
  - Quantity: `1`

- **Expected Result:**
  - Product is added to the cart successfully.
  - Cart displays the correct item details and total amount.
  - User can see the `Proceed To Checkout` option.

- **Actual Result:**
  - [To be filled during execution]

- **Execution Status:**
  - Pass / Fail / Blocked / Not Executed

- **Executed By:** [Name]
- **Execution Date:** [YYYY-MM-DD]
- **Evidence:**
  - Screenshot of cart contents and total price.

- **Notes:**
  - If the cart shows duplicate items or incorrect totals, document the discrepancy and verify with additional quantity changes.
