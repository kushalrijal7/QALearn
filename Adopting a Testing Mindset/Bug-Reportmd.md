# Bug Report: Order Accepted with Invalid Text as Zip Code During Checkout

## Environment Details
- **Application:** MindBridge
- **Environment:** Localhost (`http://localhost:3000`)
- **Test Account:** admin@mindbridge.local
- **Browser:** Chrome
- **Date/Time:** July 8, 2026

## Severity & Priority
- **Severity:** Major
  * *Reason:* The system fails to validate critical user input fields, allowing corrupt data ("testing") into the order processing database, which would prevent successful shipping/billing fulfillment in production.
- **Priority:** High

## Prerequisites / Pre-conditions
1. MindBridge application is running locally.
2. User is logged in using the admin test account.
3. At least one course has been added to the shopping cart.

## Steps to Reproduce
1. Navigate to `http://localhost:3000` and sign in.
2. Go to the course **Catalogue** and add any available course to your cart.
3. Click on the shopping cart icon and proceed to **Checkout**.
4. Fill in all required billing details.
5. In the **Zip code** input field, enter the string text: `testing`.
6. Click the **Place order** button.

## Expected Result
The system should reject the order and throw a validation message (e.g., *"Please enter a valid 5-digit zip code"*), preventing the form submission.

## Actual Result
The order is successfully accepted and processed using the text `"testing"` as a valid zip code.

## Test Data / Edge Case Notes
This report captures the specific defect where alphabetic strings bypass front-end/back-end checkout filters. Other boundary test variations include:
- `12` (Too short)
- `1234567890` (Too long)
- `@#%` (Special characters)
- `[Blank]` (Missing data validation)

## Attachments
- **Screenshots:** `checkout_error_zip_bypass.png`
- **Console Logs:** None (No JavaScript errors thrown; form submitted with standard 200 OK response status)