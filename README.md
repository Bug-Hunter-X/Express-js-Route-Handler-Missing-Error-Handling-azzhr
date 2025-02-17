# Express.js Route Handler Missing Error Handling

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input and missing resources.  The `bug.js` file showcases the problematic code, while `bugSolution.js` provides a corrected version.

## Bug Description

The original code attempts to fetch a user from an array using a user ID from the request parameters. However, it fails to handle two crucial scenarios:

1. **Invalid User ID:** If the `userId` is not a valid number (e.g., a string or a non-numeric character), `parseInt(userId)` will return `NaN`, causing the `find` method to fail silently. 
2. **User Not Found:** If no user with the matching ID exists, the `find` method will return `undefined`, again resulting in undefined behavior. 

These omissions can lead to application crashes, unexpected responses, or vulnerabilities.

## Solution

The corrected code in `bugSolution.js` addresses these issues by:

1. Validating that `userId` is a number using `isNaN`.
2. Explicitly checking if a user with the given ID exists and returning a proper 404 response if not found.

This ensures robustness and prevents unexpected errors.