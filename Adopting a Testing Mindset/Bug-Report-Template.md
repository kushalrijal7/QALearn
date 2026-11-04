# Bug Report: [Short, descriptive title of the issue]

## Environment Details
- **Application:** MindBridge
- **Environment:** Localhost (`http://localhost:3000`)
- **Test Account:** admin@mindbridge.local
- **Browser:** Chrome
- **Date/Time:** [Insert Date and Time]

## Severity & Priority
- **Severity:** [Blocker / Critical / Major / Minor / Trivial]
- **Priority:** [High / Medium / Low]

## Prerequisites / Pre-conditions
1. MindBridge application is running.
2. User is logged in using the admin test account.
3. At least one course is added to the cart.

## Steps to Reproduce
1. Navigate to `http://localhost:3000` and sign in.
2. Go to the **Catalogue** and open any course.
3. Click **Add to cart**, open the cart, and select **Checkout**.
4. In the **Zip code** field, enter the problematic value tested:
   * *Value used:* [e.g., letters, too short/long (12, 1234567890), symbols (@#%), empty]
5. Click **Place order**.

## Expected Result
The system should validate the input and either:
- Reach the order success page (if valid data).
- Display a clear, user-friendly error message preventing submission (if invalid/edge case data).

## Actual Result
[After placing the random values including letter only and short
zip codes, the application is enabling users to checkout even if the 
zip code is invalid with special characters as  well0, e.g., Application crashed, accepted invalid letters, infinite loading, etc.]

## Test Data / Edge Case Notes
This issue was identified while performing edge-case validation on the Zip Code field. Tested variations include:
- [Accepted checked out and enrolled ] Letters (e.g., "ABCDE")
- [Accepted checked out and enrolled ] Too short / too long length boundaries (e.g., "12", "1234567890")
- [94105 ] Special symbols (e.g., "@#%")
- [ it says zip code is required ] Empty/Blank field

## Attachments
- **Screenshots/Video:** [Attach or link screenshots of the error/actual behavior]
- **Console Logs:** [Paste any relevant browser console error logs here]