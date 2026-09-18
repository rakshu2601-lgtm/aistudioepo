## Application Overview
AppFestResult manages the Om.ai Beyond Limits Challenge from roster setup through submissions, peer voting, judge scoring, AI analysis, consensus approval, and the final reveal. Nine participants rank every competing app except their own, while Siddarth, Monica, and Brandon score independently and unanimously approve the official 1st–9th ranking.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Members | Roster and login mapping | — |
| Challenge Settings | Dates, phases, and rules | — |
| Applications | App submissions and proof | Participant → Members |
| Participant Ballots | Private 1–8 peer rankings | Voter → Members; ranks → Applications |
| Judge Evaluations | Weighted scorecards | Judge → Members; Application → Applications |
| AI Settings | OpenAI-compatible configuration | — |
| AI Analyses | Prediction history and rationale | Winners → Applications |
| Final Rankings | Manual 1st–9th order | Ranks → Applications; AI analysis |
| Final Approvals | Unanimous judge decisions | Ranking; Judge → Members |
| Presentation Slots | 15-minute showcase schedule | Application; Presenter → Members |
| Audit Log | Critical event history | — |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| All/Active Members | List | Members |
| Challenge Control/Timeline | List, Calendar | Challenge Settings |
| Application Gallery/Submitted/Pipeline | List, Kanban | Applications |
| My Ballot/Ballot Audit/Voting Completion | List | Participant Ballots |
| Judge Scores/Matrix/Summary/Progress | List, Spreadsheet | Judge Evaluations |
| AI Configuration/Service Status | List | AI Settings |
| AI History/Latest Prediction | List | AI Analyses |
| Ranking Drafts/Versions/Leaderboard | List | Final Rankings |
| Approval/Consensus/Audit | List | Final Approvals |
| Presentation Schedule/Calendar/Board | List, Calendar, Kanban | Presentation Slots |
| Audit Trail/Critical Events | List | Audit Log |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Participant Challenge Hub | Personalized challenge journey | Countdown, phase stepper, readiness, ballot and schedule cards |
| Judge Command Center | Scoring and decision cockpit | KPIs, comparison leaderboard, variance, AI and consensus panels |
| Results Stage | Presentation-ready reveal | Winner hero, podium, 1st–9th grid, score comparison and consensus badges |

## Design Decisions
- Uses nine confirmed participants and blocks self-voting.
- Peer prediction uses 8-to-1 Borda ranking signals.
- Judge weights: UI 15%, navigation 15%, core 20%, innovation 15%, beyond-Creator proof 20%, integrations 10%, presentation 5%.
- External OpenAI-compatible analysis never auto-publishes results.
- Publication requires approval from all three named judges.
- CSS animation includes responsive, reduced-motion, and print fallbacks.
