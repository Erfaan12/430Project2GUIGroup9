# Task 1 - Login, Security, and Shared Navigation

## Assigned scope

- Define the initial Login state.
- Describe role selection, username entry, and password entry.
- Define how the UI calls `Security.verifyPasswd(user, password)`.
- Show success transitions to Client Menu, Salesclerk Menu, or Manager Menu.
- Show failed authentication returning to Login with an error.
- Define the meaning of Back, Quit, and Logout for shared navigation.
- Propose consistent names and labels for all team diagrams.

## Expected output

1. State descriptions for Login, Invalid Login, and shared Exit/Session Navigation behavior.
2. A transition table for successful login, failed login, logout, back, and quit.
3. A diagram fragment showing login success and failure paths.
4. A paragraph explaining authentication and session history as non-FSM data.
5. Shared transition-label rules for the group.
6. Review Task 2 before final integration.

## Acceptance check

- Credentials match the assignment rules.
- Password logic is not placed directly in the UI.
- All three user roles have a clear destination.
- Invalid credentials do not enter an authorized menu.

