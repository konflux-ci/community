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
| Andrew McNamara | Red Hat | [arewm](https://github.com/arewm)           | May 2024 | May 2026 |
| Brian Cook      | Red Hat | [brianwcook](https://github.com/brianwcook) | May 2024 | May 2026 |
| Ralph Bean      | Red Hat | [ralphbean](https://github.com/ralphbean)   | May 2024 | May 2027 |

*There is no designated facilitator at the moment. The responsibility is distributed across all the*
*members of the committee.*

### Former Members
| Full Name| Company | GitHub                                  | From     | Until    |
| -------- | ------- | --------------------------------------- | -------- | -------- |
| None yet |

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

> The elections process may become more strict over time, depending on the evolving
nature of the community.

### Voter Eligibility

The elections are open for anyone to vote. The community asks that voters:

1. Vote only if they are active participants in the community.
2. Vote only once.

> *Participants* in this context refer to ones that contribute to the community either
by taking part in community discussions or by writing and reviewing code changes.

### Candidate Eligibility

Candidates must be active participants in the community, and must be nominated by an
eligible voter.

### Nominations Process

A GitHub issue will be created, calling for nominations through the issue's comments
section. A link to the issue will be shared (at least) on konflux@googlegroups.com.

Nominations should contain: email address, GitHub handle, company affiliation, and
Konflux-CI project(s) they participate in, for both the nominee and the nominating
participants.

One CAN nominate themselves.

Any nominee who accepts the nomination will be on the ballot.

### Election Process

Elections will be held as a poll in Google Forms. voters will select as many candidates
as there are open seats for. E.g. if the elections are held for replacing 2 open seats,
then voters will have to select 2 candidates in their vote (a name can only be picked
once per each voter).

In case the number of seats is greater or equal to the number of candidates,
voters will also be able to vote against each candidate being elected, and a candidate
will only be elected if more votes are casted for the candidate than against.

Details about the schedule and logistics of the election will be announced in a timely
manner by the election officers to eligible candidates and voters via the
konflux@googlegroups.com mailing list.

Access to the poll results will be given to the election officers and to a member of
the committee, if possible, not one nominated to be reelected.

### Election Officers

For every election, the governance committee will choose election officers as they deem
appropriate and sufficient (e.g. headcount and identity), with the exception that
an election officer should not be running for the current elections.

The election officers will:

- Share elections-related announcements.
- Create the election poll and process its results.
- Have the final say regarding issues related to the elections they were appointed for
  and are unaccounted for in this document.
- Enhance this document to account for any such issues found during the same elections.

### Changes to Governing Committee

When someone joins the governing committee:

- They should be added to
  [the list of current governing committee members](#current-members).
- They will be added to
  [konflux-governance-committee](https://github.com/orgs/konflux-ci/teams/konflux-governance-committee)
  GitHub team.

When someone leaves the governing committee:

- They should be moved from
  [the list of current governing committee members](#current-members) to
  [the list of former members](#former-members).
- They will be removed from
  [konflux-governance-committee](https://github.com/orgs/konflux-ci/teams/konflux-governance-committee)
  GitHub team.

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
