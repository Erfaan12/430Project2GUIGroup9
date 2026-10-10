# Task 4 - Manager GUI

## Assigned scope

- Define the Manager Menu state.
- Include modify sale price, receive shipment, and freeze/unfreeze client account.
- Define password confirmation before every manager operation.
- Define Become Salesclerk and its password check.
- Define return behavior after the manager finishes acting as a salesclerk.
- Define Back, Quit, and Logout behavior.

## Expected output

1. State descriptions for Manager Menu, Manager Confirmation, and Become Salesclerk.
2. A transition table for manager choices and correct/incorrect confirmation passwords.
3. A manager-state diagram fragment.
4. A paragraph explaining authorization/confirmation data as a non-FSM issue.
5. A list of manager actions that can occur inside one confirmed-operation state instead of separate states.
6. Review Task 1 before final integration.

## Acceptance check

- Every manager operation requires confirmation.
- Manager can become a salesclerk only after the required password check.
- Logout from delegated Salesclerk Menu returns to Manager Menu.
- A directly logged-in manager can log out to Login.

