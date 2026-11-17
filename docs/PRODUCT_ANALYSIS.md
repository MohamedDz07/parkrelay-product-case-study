# ParkRelay — retrospective product analysis

This document combines **three decisions confirmed by Mohamed DE** with a retrospective analysis of publicly described product behaviour. It is not the original PRD or a copy of client documents. Proposed criteria and metrics below are not claims of implementation.

## Product framing

**User jobs**

- As a driver leaving a public street space, I want to share a useful signal quickly without completing a long form.
- As a driver searching nearby, I want to see recent opportunities and navigate toward one while understanding that availability is uncertain.

**Core hypothesis to test:** if enough drivers share timely signals in a defined area, searchers will encounter useful parking opportunities more often than they would without those signals. This is a hypothesis for analysis, not a measured conclusion.

**Visible first-phase scope:** Ottawa; free public street parking signals; no reservations or payments. Mohamed confirmed that the **paid swap** flow was deferred to a planned V2. The public product describes a Relay Out action, map-based discovery, distance filtering, navigation, and notifications. [Product site](https://parkrelay.ca/) · [Google Play listing](https://play.google.com/store/apps/details?id=com.partrelay.app)

## What the supplied screen actually shows

The [Relay Out capture](../assets/relay-out-flow.png), supplied with permission to use it on GitHub, shows a map screen with a prominent Relay Out action. Opening it presents **Now**, **2 min** and **5 min** as departure-time choices. With **Now** selected, the sheet says the signal stays active for **7 minutes** and provides a separate **Send Signal** button. This is a two-step visible flow; the website's shorthand “one tap” should not be read as a complete interaction count.

The screen documents the interface and the communicated rule. It does not prove what happens after Send Signal, whether the server enforces the seven-minute window, or what changes when the other time choices are selected.

## Decisions confirmed by the contributor

| Decision Mohamed owned | What it means for the MVP | Boundary of the evidence |
|---|---|---|
| Limit V1 to free public street parking; defer paid swap to V2 | V1 centres on community signals and discovery. | The exact design or release date of V2 is not established. |
| Design Relay Out | The departing driver has a defined action to share a parking opportunity. | Original screens and design files are not included. |
| Define signal validity duration | A report has an expiry rule because availability changes. | The supplied screen displays seven minutes when Now is selected; backend enforcement is not verified here. |

## Product reasoning

| Visible choice | User problem addressed | Trade-off or risk to examine |
|---|---|---|
| Signal, not reservation | A driver can learn where a space may open without promising ownership of a public space. | The space can be taken before arrival; language must set expectations. |
| Short-lived community report | Availability changes quickly. | Too few reports make the map sparse; stale or duplicate reports reduce trust. |
| Free street parking in phase one | A limited use case is easier to understand and test. | It excludes garages, paid parking, and other demand. |
| Nearby map and navigation | Searchers need location context and a next action. | Location accuracy, battery use, and privacy need careful handling. |

This table interprets the public experience and its trade-offs; it does **not** assign additional decisions or implementation to one person. The three personally owned decisions are stated separately above.

## Example acceptance criteria for a future iteration

These criteria are **proposed examples**, not the project's original backlog:

1. A search result clearly states that a signal is neither a reservation nor a guaranteed empty space.
2. A report displays its age and disappears after the defined validity window.
3. A driver can stop sharing an active signal.
4. The flow handles missing location permission and weak connectivity with an understandable message.
5. A feedback path lets a searcher mark a signal as useful, stale, or incorrect.

## Measurement plan (proposed)

| Question | Suggested measure | Interpretation limit |
|---|---|---|
| Are drivers contributing? | Valid Relay Out signals per area and week; repeat contributors | Volume alone does not show usefulness. |
| Are searchers seeing signals? | Searching sessions with at least one relevant recent signal | Depends on area, time, and density. |
| Are signals useful? | Feedback after navigation; report age; stale-report rate | Self-reported feedback may be biased. |
| Does the product save time? | Search duration compared with a measured baseline | Requires comparable locations and periods; cannot infer from registrations. |

The contributor confirmed **167 registered accounts** and **246 parking reports in the first week**. These are activity counts. No public analytics export is attached, and the product's impact on time, fuel, emissions, or parking success is not established by these counts.

## Evidence boundaries

- **Independently visible:** iOS and Android store listings; public website and its described flows.
- **Contributor-supplied evidence:** Relay Out capture showing time choices and a seven-minute note.
- **Contributor-reported:** personal scope, the three decisions above, reported stack, 167 registrations, and 246 reports.
- **Not established here:** original decision logs, exact launch date, backend expiry behaviour, individual code ownership, retention, parking success rate, time saved, or environmental impact.

See the [case study](../README.md) for the concise narrative and source links.
