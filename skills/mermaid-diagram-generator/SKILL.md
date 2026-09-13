---
name: mermaid-diagram-generator
description: Automatically turn text descriptions into mermaid diagram code (flowcharts/sequence/class/state/ER/gantt). Use when the user describes systems, processes, relationships, states, or database schemas.
version: 1.0.0
metadata:
  author: mike22890
  tags: documentation diagram visualization mermaid
---

# Mermaid Diagram Generator

Turn natural-language descriptions into mermaid code blocks.

## When to use

Auto-diagram when the user describes:
- "how does X flow" → flowchart
- "how do X and Y interact" → sequence diagram
- "relationships between X classes" / "module dependencies" → class diagram
- "how do states transition" → state diagram
- "database table relations" → ER diagram
- "project timeline" → gantt

## Supported diagram types

| Type | Keywords | Use |
|---|---|---|
| `flowchart` | flow/steps/decision/branch | business flows, decision trees |
| `sequenceDiagram` | interaction/call/message/response | API calls, protocols |
| `classDiagram` | class/inheritance/interface/dependency | OO design, module relations |
| `stateDiagram-v2` | state/transition/trigger | state machines, workflow engines |
| `erDiagram` | table/field/foreign key/relation | database schemas |
| `gantt` | schedule/milestone/dependency | project management |
| `pie` | share/distribution | data visualization |

## Generation flow

1. **Identify diagram type** from keywords
2. **Extract entities and relations**: nodes, edges, directions
3. **Generate mermaid code** in a ` ```mermaid ` block
4. **Self-check**: quote labels with special chars / correct direction (TD/LR/BT/RL) / split complex diagrams

## Examples

### Input
"User login flow: enter credentials → backend verifies → failure returns error, success returns token"

### Output
```mermaid
flowchart LR
    A[Enter credentials] --> B{Backend verify}
    B -->|Fail| C[Return error]
    B -->|Success| D[Return token]
```

### Input
"User places order: client → API gateway → order service → payment service → inventory service"

### Output
```mermaid
sequenceDiagram
    participant C as Client
    participant G as API Gateway
    participant O as Order Service
    participant P as Payment Service
    participant I as Inventory Service

    C->>G: POST /order
    G->>O: Create order
    O->>P: Request payment
    P-->>O: Payment result
    O->>I: Deduct inventory
    I-->>O: Inventory confirmed
    O-->>G: Order complete
    G-->>C: 200 OK
```

## Typography rules

- **Direction**: business flows LR (horizontal), decision trees TD (vertical)
- **Labels**: quote anything over 5 chars `["label"]`
- **Colors**: only when necessary (defaults are clear)
- **Comments**: `%% comment`
- **Never**: emoji in node labels, overlong labels (>15 chars), decorative shapes

## When not to diagram

- Description too vague ("that thing") → ask first
- Too simple (≤3 nodes) → a text list is clearer
- User explicitly says "no diagram" → listen

## After output

Ask: "Anything to add or change?" / "Want the related X flow too?" (linked diagrams)
