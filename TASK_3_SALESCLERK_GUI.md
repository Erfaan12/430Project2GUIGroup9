# Task 3 - Salesclerk GUI

## Assigned scope

- Define the Salesclerk Menu state.
- Include list products with quantity on hand, add client, add product, and load database.
- Include other allowed warehouse operations, excluding manager-only operations.
- Define the Become Client state and client-ID validation.
- Define return behavior after the salesclerk finishes acting as a client.
- Define Back, Quit, and Logout behavior.

## Expected output

1. State descriptions for the Salesclerk Menu and Become Client flow.
2. A transition table for all salesclerk choices and valid/invalid client IDs.
3. A salesclerk-state diagram fragment.
4. A paragraph explaining loops and variable-length lists as a non-FSM issue.
5. A list of simple operations that remain in the Salesclerk Menu without a separate state.
6. Review Task 4 before final integration.

## Acceptance check

- Manager-only operations are not available.
- Become Client requires a valid client ID.
- Logout from delegated Client Menu returns to Salesclerk Menu.
- A directly logged-in salesclerk can log out to Login.

