# Task 1 - Login, Security, and Session Navigation

Assigned to: Muhammad Irfan Younas

## Scope

This part defines the first panel of the warehouse MPIS, authentication through the separate Security object, routing to the correct role menu, and the shared logout and quit rules. The manager-operation confirmation panel is part of Task 4, not this task.

## Login Panel state

Purpose: The Login Panel identifies the user and sends the user to the correct menu after successful authentication.

Displayed information: A choice of Client, Salesclerk, or Manager and fields for username and password.

User interaction: The user selects a role, enters a username and password, and selects Login or Quit.

Processing: UserInterface sends the selected role and credentials to `Security.verifyPasswd(role, username, password)`. The UI does not compare passwords itself.

Successful result: A client goes to Client Menu, a salesclerk goes to Salesclerk Menu, and a manager goes to Manager Menu. The current role and original role are stored in SessionContext.

Failure result: The Login Panel displays an error, clears the password field, and remains in the same state. A separate Invalid Login state is unnecessary because the user interaction has not changed.

Quit result: Quit ends the interface session.

## Credential rules

- A client uses the client ID as both username and password. Security also verifies that the client ID exists.
- A salesclerk uses `salesclerk` as both username and password.
- A manager uses `manager` as both username and password.
- Manager confirmation for individual manager operations is handled in Task 4.

## Transition table

| Current state | Event and condition | Action | Next state |
| --- | --- | --- | --- |
| Start | Program begins | Create the UI and empty SessionContext | Login Panel |
| Login Panel | Client credentials are valid | Store client role and client ID | Client Menu |
| Login Panel | Salesclerk credentials are valid | Store salesclerk role | Salesclerk Menu |
| Login Panel | Manager credentials are valid | Store manager role | Manager Menu |
| Login Panel | Credentials are invalid | Display error and clear password | Login Panel |
| Login Panel | Quit is selected | Clear session data and close the UI | End |
| Client Menu | Logout with no delegated role | Clear session data | Login Panel |
| Client Menu | Logout while salesclerk is acting as client | Pop delegated client role | Salesclerk Menu |
| Salesclerk Menu | Logout with no delegated role | Clear session data | Login Panel |
| Salesclerk Menu | Logout while manager is acting as salesclerk | Pop delegated salesclerk role | Manager Menu |
| Manager Menu | Logout | Clear session data | Login Panel |

## Design responsibilities

### UserInterface

Displays the current panel, collects input, calls Security, and sends the event and verification result to SessionContext. It displays the next panel selected by the context.

### Security

Owns `verifyPasswd(role, username, password)`. It checks the fixed manager and salesclerk credentials and asks the warehouse/client collection whether a client ID is valid. It returns success or failure without choosing the next panel.

### SessionContext

Stores the current panel, authenticated role, active client ID, and role-return history. It computes the next panel using the current panel, event, and stored information. Delegated logout restores the immediately previous role; ordinary logout clears the session and selects Login Panel. This follows the centralized context approach in textbook Section 8.9.1. Warehouse operations remain in the warehouse facade.

## Shared Back and Logout rules

Back or Quit within a sub-panel returns to its parent panel without ending the authenticated session. Login Panel has no Back option because it is the entry panel. Its Quit option closes the program. Logout from a role menu returns to Login Panel for a directly logged-in user or restores the immediately preceding role for delegated access. Panel-return history and role-return history are separate. Tasks 2 through 4 supply their sub-panel transitions.

Only one panel is active at a time. Failed login remains in Login Panel. The logout guards are mutually exclusive: a prior delegated role either exists or does not exist. SessionContext evaluates the guard to select one next panel.

### Warehouse and ClientList

Warehouse provides the facade operation used by Security to verify that a client ID exists. ClientList performs the actual client search because it owns the client collection.

## What does not fit a pure FSM

The set of GUI panels is finite, but usernames, passwords, client IDs, and stored clients are data with many possible values. Making a state for every possible credential or client would not be practical. Security checks these values as data and returns a Boolean result that selects the valid-login or invalid-login transition. The interface also needs to remember whether a user is temporarily acting as another role. SessionContext stores the original role, active role, active client ID, and a small role stack. The FSM therefore controls panel changes, while ordinary objects and variables store the changing information.

## Diagram connection notes

- Task 2 connects Client Menu to the client sub-panels.
- Task 3 connects Salesclerk Menu to salesclerk operations and Become Client.
- Task 4 connects Manager Menu to manager operations, confirmation, and Become Salesclerk.
- The final group diagram should use Login Panel as the common entry point and follow the logout destinations in the transition table.

