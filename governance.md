# Konflux Governance

The Konflux governance committee is the governing body of the Konflux open source project. It is an
elected group that represents the contributors to the project, and has an oversight on governance
and technical matters.

## Konflux Governance Committee

The Konflux governance committee consists of three elected individuals and one optional facilitator.
The three seats are held for two year terms, staggered by one year: every year either one or two
of the seats are up for election.

### Founder Exception

In order to start the Konflux community, the committee was initially populated with its founders.
This is a one-time exception to help start the community when an election was not deemed necessary.
These exceptions were granted to Ralph Bean, Brian Cook, and Andrew McNamara. To allow the desired
staggering of elected members, the individual with the alphabetically-top last name was given a
membership of one year while the others were given two years. By May 2026, the latest, all committee
members will have been elected.

### Current Members

| Full Name       | Company | GitHub                                      | From     | Until    |
| --------------- | ------- | ------------------------------------------- | -------- | -------- |
| Ralph Bean      | Red Hat | [ralphbean](https://github.com/ralphbean)   | May 2024 | May 2025 |
| Andrew McNamara | Red Hat | [arewm](https://github.com/arewm)           | May 2024 | May 2026 |
| Brian Cook      | Red Hat | [brianwcook](https://github.com/brianwcook) | May 2024 | May 2026 |

*There is no designated facilitator at the moment. The responsibility is distributed across all the*
*members of the committee.*

## Governance Facilitator Role (optional)

The governance facilitator role is a non-voting, non-technical advisory position that helps ensure
all governance committee meetings are inclusive, and key milestones toward governance are met. The
facilitator is a role, meaning it may be occupied by a single individual, or a series of individuals
over time. The goal of this position is servant leadership for the project, community, and
stakeholders. The committee may choose to make this a permanent role at their discretion.
Deliverables may include creation of mailing lists, project tracking boards, governance draft
documents, and so forth.

## Maximum Representation

It is the desire of the committee to limit the amount of influence of any single employer/company over the
project. However, currently, there is not enough diversity to make this a reality. This section
should be revised in the future when more than one employer/company are active members of the
Konflux community.

## Committee Responsibilities and Deliverables

The committee MUST:

- Balance technical, architectural, and governance expertise.
- Hold staggered terms, sufficient to ensure an orderly transition of power via elections.
- Provide designated alternates in cases where quorum is required but not attainable with the
  current set of members.

The committee is responsible for a series of specific artifacts and activities:

- The [Code of Conduct](./code_of_conduct.md) and handling violations
- Define the processes around ADRs ([Architectural Design Records](https://adr.github.io/)) in the
  [architecture](https://github.com/konflux-ci/architecture/tree/main/ADR) repository. Should the
  community fail to reach consensus on whether to accept a proposed ADR or not, the governance
  committee can help break the impasse.

## Governance Decision-Making Process

Governance decisions are reviewed and accepted in terms of pull requests to this repository.
Decisions can be proposed by anyone, not just community or committee members.

The governance committee decisions are taken by seeking consensus towards a motion from all its
members. If the consensus cannot be reached, the motion may be altered or dropped.

Architectural decisions are handled similarly but on the
[architecture](https://github.com/konflux-ci/architecture) repository. The acceptance, or
rejection, of architectural decisions abide to the same rules of the governance decision-making
process.

## Elections

The election process is not yet established. It MUST be done by the next election cycle. It MUST
define, at least, the following:

1. The actions required to fulfill a change in the committee composition. For example, when a new
   committee member joins, which groups should they be added to, and, conversely, when a member
   leaves, which groups should they be removed from.
2. The eligibility requirements of voters and nominees.
3. The voting process.

## Governing Committee Leave Policy

Any member of the governing committee is welcome to take leave from being a governing committee
member, for any reason (which they are not required to disclose). The actions taken will depend on
both of:

1. The length of the leave: whether this is greater or less than approximately (at the discretion of
   the other governing committee members) 1/4 of their total term (since terms are 2 years, this
   means the criteria is whether or not the leave is greater than 6 months).
2. Whether their seat will be up for election during the period of their leave

If the leave is less than or equal to 1/4 of the committee member's total term, and their seat will
not be up for re-election during that time, the governing committee member may select someone to be
an acting governing committee member for the length of the leave. This person must be eligible for
an election even though an election will not take place.

If the length of the leave is greater than 1/4 of the total term, or their seat will be up for
election during the leave period, the governing committee member will be required to step down from
their seat and an election will be held.

## Origin

This governance document was highly inspired, with love, by the [governance
document](https://github.com/tektoncd/community/blob/main/governance.md) for the Tekton project.