# Aspects That Do Not Fit a Pure FSM

This section is a shared group deliverable. Discuss at least the following categories and explain how normal program objects and variables supplement the FSM.

## Dynamic data

The number of clients, products, invoices, payments, and orders is not finite in the same way as the fixed panel states. The warehouse domain objects and collections store this data; the FSM stores only the current interface state.

## User-entered values

Usernames, passwords, client IDs, quantities, prices, and shipment amounts have many possible values. They should be treated as input data and validated by the appropriate objects instead of becoming separate FSM states.

## Authentication and authorization

The Security object verifies credentials. The FSM uses the returned success or failure result to choose a transition. Manager operations request confirmation and proceed only after successful verification.

## Delegated-role history

When a salesclerk becomes a client, or a manager becomes a salesclerk, the program must remember the original role so Logout returns to the correct menu. Store this information in a session/context object or a small navigation stack rather than creating a different copy of every state.

## Repeated and variable-length operations

Lists and item-by-item operations may repeat an unknown number of times. Implement them with loops and iterators inside a state. Create a new state only when the way the interface interacts with the user changes.

## Error messages

Invalid credentials, IDs, quantities, and other bad inputs do not require permanent states unless the interface becomes a different panel. Most errors can be displayed within the current state, followed by another input attempt.

