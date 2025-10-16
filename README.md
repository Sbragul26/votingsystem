# Test Results - Blockchain Voting System

This document outlines the successful testing of our blockchain-based voting system's authentication and navigation features. We ran automated tests to ensure everything works smoothly, from user registration to secure access to voting pages. Below, you’ll find the results, presented in a way that’s easy to follow.

## Table 1: Authentication Test Cases (8 Cases)

| TC ID       | Test Scenario                     | Input / Action                                                                 | Expected Output                                                                 | Actual Output                                                                   | Result |
|-------------|-----------------------------------|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------|--------|
| REG-V-01    | Display Registration Form         | User visits /register.                                                         | Registration form with Name, Email, and Password fields shows up.                | Form fields and "Create Account" button appeared as expected.                    | Pass   |
| REG-V-02    | Check Empty Fields                | Click "Create Account" without filling in any fields.                           | Error messages for all required fields pop up. No blockchain transaction sent.   | "Name is required", "Email is required", and "Password is required" displayed.    | Pass   |
| REG-V-03    | Test Weak Password                | Enter Password: "vote". Click "Create Account".                                 | Error: "Password must be at least 8 characters" shows. No transaction sent.      | Password strength error appeared correctly.                                      | Pass   |
| REG-V-04    | Successful Registration           | Fill form with valid, unique details and submit.                                | "Voter registered successfully!" message appears. Blockchain records new user.   | Blockchain transaction succeeded, and success message displayed.                 | Pass   |
| REG-V-05    | Prevent Duplicate Registration    | Submit form with an already-used email.                                        | "Voter with this email or name already exists" message shows.                    | Expected 409 Conflict error message appeared.                                    | Pass   |
| LOG-V-01    | Display Login Form                | User visits /login.                                                            | Login form with Email and Password fields appears.                               | Form fields and "Sign In" button rendered correctly.                             | Pass   |
| LOG-V-02    | Successful Login                  | Enter Email: "voter@example.com", Password: "securepassword123".                | User is taken to /voting-dashboard.                                              | Navigation to voting dashboard worked after successful blockchain verification.  | Pass   |
| LOG-V-03    | Test Invalid Credentials          | Enter Email: "voter@example.com", Password: "wrongpass".                        | "Invalid email or password" error shows.                                         | Expected 401 Unauthorized error message displayed.                               | Pass   |

## Table 2: Navigation Test Cases (5 Cases)

| TC ID       | Test Scenario                     | Action / State                                                                 | Expected Output                                                                 | Actual Output                                                                   | Result |
|-------------|-----------------------------------|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------|--------|
| ROU-U-01    | Public Page Access                | Non-logged-in user visits /login.                                               | Login page loads properly.                                                      | Login page displayed as expected.                                               | Pass   |
| ROU-U-02    | Block Unauthorized Access         | Non-logged-in user tries to access /voting-dashboard directly.                  | User is redirected to /login.                                                   | Login page loaded instead of voting dashboard.                                  | Pass   |
| ROU-U-03    | Allow Authorized Access           | Logged-in user navigates to /voting-dashboard.                                  | Voting dashboard loads correctly.                                               | Voting dashboard displayed as expected.                                         | Pass   |
| ROU-U-04    | Handle Invalid Routes             | Any user visits a nonexistent page like /randompage.                            | System shows the Home page as a fallback.                                        | Home page loaded correctly.                                                     | Pass   |
| ROU-U-05    | Root Path Access                  | Any user visits /.                                                             | Home page loads properly.                                                       | Home page displayed as expected.                                                | Pass   |

## Summary and Takeaways

- **All Tests Passed!** Our test results show *Test Suites: 3 passed, 3 total* and *Tests: 13 passed, 13 total*. This confirms that the voting system’s authentication and navigation features are working as designed, ensuring a secure and smooth experience for voters.
- **Console Notes:** We noticed some informational warnings about React Router’s future flags in the console. These are harmless and don’t affect the system’s performance.
- **Clear Feedback:** The ✅ PASSED messages we added to the tests are visible in the output, making it easy to connect each test case to its result.

This testing ensures our blockchain voting system is secure, user-friendly, and ready for voters to use with confidence.
