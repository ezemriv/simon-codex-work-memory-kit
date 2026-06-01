# Architecture Studio Example

This example is a compact fictional Simon-style architecture and interior-design studio memory setup. It shows how a project vault can track related client work, capture collaborator context, record design decisions, promote reusable lessons to a global wiki, and block or generalize sensitive details.

## Scenario

The studio is managing three related projects:

- Project Atrium: a small office reception refresh with acoustic and material constraints.
- Project Garden Flat: a residential kitchen and living-room update focused on durable finishes.
- Project Lantern Row: a townhouse entry and corridor lighting refresh.

The shared collaborators are role-based and fictional: Lead Designer, Materials Lead, Lighting Consultant, Site Coordinator, and Client Sponsor. No real names, exact addresses, access details, private budgets, or supplier quotes are stored.

## Memory Layout

- `project/AGENTS.md`: local operating rules for agents working in the studio project.
- `project/memory/glossary.md`: local project terms, roles, and privacy-safe aliases.
- `project/memory/decisions.md`: design decisions across the three related projects.
- `project/memory/wiki-queue.md`: lessons ready for promotion, plus blocked or generalized details.
- `global-wiki/wiki/index.md`: the global vault index for reusable studio knowledge.
- `global-wiki/wiki/material-samples.md`: a promoted cross-project lesson.

## Privacy Pattern

Sensitive details are either blocked or generalized:

- Exact address becomes "urban corner unit" or "townhouse entry".
- Client names become "Client Sponsor" or "client household".
- Supplier quotes become "mid-range material quote".
- Access codes, private routines, and private photos become `[BLOCKED: sensitive site detail]`.

The useful lesson survives. The private detail does not.
