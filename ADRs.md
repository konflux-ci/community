# ADR Process

ADRs are Architectural Decision Records. We adopted them originally in [ADR 1](https://github.com/konflux-ci/architecture/blob/main/ADR/0000-adr-template.md).
The process for proposing, accepting, and rejecting ADRs is now documented here. We'll keep this doc updated as we revise that process. ADRs are [stored in the architecture repo](https://github.com/konflux-ci/architecture/tree/main/ADR) and rendered at [konflux-ci.dev/architecture/ADR](https://konflux-ci.dev/architecture/ADR/index.html).

## When to file an ADR?

* When you want to introduce or change an architectural principle of the project.
* When you want to introduce a feature that requires coordination across multiple subsystems.
* When you want to record a decision that has so far existed only informally, to document it for the community.
* When you want to introduce a new dependency.
* When you want to expand the definition of Konflux "Core".

The best ADRs explain _why_ and have detailed *consequences* sections, illustrating the impact of the decision.

## When to not file an ADR?

* For small changes introducing a new parameter or option.
* For cleanup projects.
* Extending on patterns that are already recorded as ADRs (unless the extension somehow substantially changes the nature of the pattern).
* When you want to create a new Konflux "Add-On" (unless you want to encourage optional integrations with other Konflux subsystems).
* You want feedback on something you're doing or trying in your own downstream Konflux deployment.

## Process

The ADR process is managed by the [Konflux Governance Committee (KGC)](https://github.com/konflux-ci/community/blob/main/governance.md).

* Anyone can submit an ADR idea.
* When new ADRs are filed, the author opens the request for comments period by announcing it on a community call.
* KGC is responsible for marking the PR with a milestone indicating the end of the request for comments period.
* The request for comments period is 2 weeks.
* The author is responsible for responding to all threads.
* At the end of two weeks, KGC will deliberate on the feature.
* Within two weeks, the KGC will either approve it, reject it, or extend the comment period for another 2 weeks and announce it on the community call.
* In all cases, the KGC is responsible for making the decision. This includes situations where some community comments are against the idea while others support it.

When an ADR is **accepted**, it means that it's the intended direction of the project.

When an ADR is **rejected**, it can mean one of multiple things:

* It's not the intended direction of the project.
* There is some ambiguity about the idea and insufficient resolution before the comments period elapsed.

The KGC must comment on why they're closing the ADR when rejecting.

ADRs receive a number when they're accepted. Rejected ADRs do not consume a number in the sequence of accepted ADRs.

## Lifecycle

ADRs can be in any one of the following states.

* **Proposed** - the ADR is unmerged. It is proposed in the queue for consideration and exists in a PR.
* **Withdrawn** - the ADR is unmerged. The author withdrew it from consideration and closed their own PR.
* **Deferred** - the ADR is unmerged. It was rejected by the KGC and does not appear in `main`.

* **Accepted** - the ADR is merged. It is accepted by KGC, but may need more detail before being implementable.
* **Implementable** - the ADR is merged. It has sufficient detail that someone can do something about it.
* **Implemented** - the ADR is merged. It is implemented. The ADR reflects facts about the system.
* **Replaced** - the ADR is merged. It was previously accepted, but has been outmoded by newer ADRs. It stays in the repo.

## ADR Template

```markdown
# NN. Title Goes Here

Date: 1999-01-01

## Status

[//]: # (One of: Proposed, Withdrawn, Deferred, Accepted, Implementable, Implemented, Replaced)
Proposed

## Context

Write about what problems you're facing and what constraints are imposed on you. Dig into why.

## Decision

Write a brief statement summarizing the decision in one or two sentences.

Add subsections if more detail is needed.

## Consequences

* Write bullets about what new things are true as a result of the decision.
* Include both good things and bad things and be clear about what is desirable and what is a compromise.
```
