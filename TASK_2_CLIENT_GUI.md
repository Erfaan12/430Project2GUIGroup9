# Task 2 - Client GUI

## Assigned scope

- Define the Client Menu state.
- Define Account Information and its sub-panels for invoices and payments.
- Define shopping-cart/order modification behavior.
- Include product-price lookup and other client-only operations.
- Define Back, Quit, and Logout transitions for every client state.
- Note how a directly logged-in client differs from a salesclerk acting as a client.

## Expected output

1. State descriptions for all client panels.
2. A transition table covering valid actions, invalid input, Back, and Logout.
3. A client-state diagram fragment.
4. A paragraph explaining dynamic client/order data as a non-FSM issue.
5. A note identifying which client actions can remain in the Client Menu without creating another state.
6. Review Task 3 before final integration.

## Acceptance check

- Client cannot access salesclerk or manager operations.
- Account, invoice, and payment navigation returns to the correct client panel.
- Logout returns to Login for a client, but to Salesclerk Menu for a delegated salesclerk.

