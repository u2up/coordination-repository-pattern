# Comparisons and Related Practices

The Coordination Repository Pattern combines several familiar ideas into one
architectural boundary: a dedicated Git repository that owns durable project
coordination state.

It does not replace every planning, documentation, or workflow tool. It defines
where long-lived coordination state is anchored so humans, automation, and AI
agents can work from the same reviewable project record.

## Quick comparison

| Practice | What is similar | What is different |
| --- | --- | --- |
| Directory inside the implementation repository | Stores plans, specs, or notes in Git near the code. | Coordination history is coupled to source branches, repository access, and implementation boundaries. |
| GitOps | Uses Git as an authoritative source of truth. | GitOps usually manages operational or infrastructure state; this pattern manages project coordination state. |
| Architecture Decision Records (ADRs) | Captures durable decisions in version control. | ADRs usually cover decisions only; a coordination repository also covers requirements, work status, review evidence, release intent, and traceability. |
| Docs-as-code | Keeps documentation in plain text and reviews it like code. | Docs-as-code is often mixed into implementation repositories; this pattern gives coordination state its own authority boundary. |
| Issue trackers and project boards | Track work, ownership, status, labels, comments, and milestones. | They are often hosted applications optimized for human workflows; the coordination repository is portable Git content usable offline and reviewable through normal Git changes. |
| Wikis and workspace tools | Preserve project knowledge and discussion. | They are usually tool-specific and less suited to branching, merging, pull-request review, and repository-level portability. |
| Knowledge graphs and project memory systems | Preserve relationships and long-term context. | They are often database-backed or runtime-specific; this pattern starts with plain-text Git artifacts as the durable source. |
| AI agent memory and multi-agent frameworks | Give agents persistent or shared context. | Memory often belongs to an agent, IDE, model provider, or orchestration runtime; the coordination repository belongs to the project. |

## When to keep coordination inside the implementation repository

A directory such as `plans/`, `specs/`, or `docs/project-state/` can be enough
when:

- the project has one implementation repository;
- the same access rules apply to code and coordination state;
- coordination changes should follow the same branches and release cadence as
  source changes;
- the project is small enough that separate history would add more friction
  than clarity.

The dedicated repository boundary becomes more useful when coordination spans
multiple codebases, must evolve independently of source branches, needs a
separate review or retention policy, or should remain portable across tools.

## How the tools can work together

A coordination repository can link to and be supported by other systems instead
of replacing them:

- issue trackers can remain public intake and notification channels;
- code review systems can remain authoritative for implementation review;
- CI systems can remain authoritative for test results and build artifacts;
- wikis and docs sites can publish generated or curated views;
- AI agents can read and update coordination artifacts through normal Git
  workflows.

The important rule is authority: each piece of project state should have one
clear owner, even if many systems display or reference it.
