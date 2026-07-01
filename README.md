# Projects Have Memory Too

A Git-native architectural pattern for separating project coordination state
from implementation state.

> Projects should own their durable coordination state, independently of the
> agents, models, and tools that participate in the work.

This matters especially in agentic coding. Today's AI coding agents have tools,
memory, and orchestration.

Projects need something different:
durable, shared, reviewable coordination state.

The Coordination Repository Pattern does this using a dedicated Git repository.

## At a glance

```text
        Humans · automation · AI agents
                     |
                     v
          Coordination Repository
  requirements · decisions · work status · evidence
                     |
              links to / governs
                     v
          Implementation Ecosystem
   code repositories · reviews · CI · releases · docs
```

## Why a separate repository?

A separate repository gives coordination state an independent lifecycle:

- coordination changes can be reviewed without touching source branches;
- one coordination domain can span one or many implementation repositories;
- access, history, retention, and sensitivity rules can differ from code;
- durable project state remains portable outside any one hosted tool.

## Read next

- **Why?** [Agentic Coding Needs Durable Coordination State](docs/AGENTIC_COORDINATION_PITCH.md)
- **How?** [Coordination Repository Pattern](docs/COORDINATION_REPO_PATTERN.md)
- **Compare:** [Related practices and alternatives](docs/COMPARISONS.md)
- **Implementation:** [`pi-env`](https://github.com/u2up/pi-env)
