# CSCI 430 - Project 2: Warehouse GUI Analysis

This repository is for Group 9's analysis and design of a Multi Panel Interactive System (MPIS) for the warehouse. The interface is modeled as a finite state machine (FSM).

## What the professor requires

1. List every GUI state and explain the purpose of each state.
2. Draw one state-transition diagram for the complete FSM.
3. Include at least six panels.
4. Explain which parts of the warehouse system do not fit the definition of a finite state machine and describe how the software will handle them.

The assignment permits either a graphical interface or a text interface. This stage asks for analysis and design; it does not require a working GUI implementation.

## Equal four-person task split

| Task | Area | Main responsibility | Work file |
| --- | --- | --- | --- |
| 1 | Login, Security, and session navigation | Login/security states, role routing, invalid-login loop, logout/quit rules, session history, and authentication as a non-FSM issue | `TASK_1_LOGIN_NAVIGATION.md` |
| 2 | Client GUI | Client states, account/invoice/payment/cart/product transitions, delegated logout behavior, and dynamic client data as a non-FSM issue | `TASK_2_CLIENT_GUI.md` |
| 3 | Salesclerk GUI | Salesclerk states, product/client/database operations, become-client flow, and repeated operations as a non-FSM issue | `TASK_3_SALESCLERK_GUI.md` |
| 4 | Manager GUI | Manager states, confirmation flow, price/shipment/freeze operations, become-salesclerk flow, and authorization as a non-FSM issue | `TASK_4_MANAGER_GUI.md` |

Each person produces the same five items: state descriptions, a transition table, a diagram fragment, error/return behavior, and one paragraph for the non-FSM discussion. Each person also reviews one other person's work. The four parts are then combined into one diagram and one final state list.

## Shared group work

- Agree on state names before drawing the final diagram.
- Combine all transitions into `FSM_STATE_LIST.md`.
- Draw one complete state-transition diagram in `diagrams/`.
- Combine each person's non-FSM paragraph in `NON_FSM_ANALYSIS.md`.
- Check that every panel has the correct Back, Quit, or Logout transition.
- Verify that delegation returns to the correct menu: client logout returns a delegated salesclerk to the Salesclerk Menu, and salesclerk logout returns a delegated manager to the Manager Menu.
- Perform one final review against `REQUIREMENTS_CHECKLIST.md`.

## Suggested workflow

1. Each person creates a branch named after the assigned task, such as `task-2-client-gui`.
2. Edit only the assigned task file and any matching draft diagram.
3. Open a pull request into `main`.
4. Have at least one teammate review the transitions before merging.
5. After all four task pull requests are merged, complete the shared integration files.

## Repository layout

```text
Project2GUIGroup9/
  README.md
  FSM_STATE_LIST.md
  NON_FSM_ANALYSIS.md
  REQUIREMENTS_CHECKLIST.md
  DIAGRAMS.md
  TASK_1_LOGIN_NAVIGATION.md
  TASK_2_CLIENT_GUI.md
  TASK_3_SALESCLERK_GUI.md
  TASK_4_MANAGER_GUI.md
```

