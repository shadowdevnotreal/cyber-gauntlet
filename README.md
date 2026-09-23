# ⚔️ Cyber Gauntlet: The Hoodie Challenge Arena

**Tagline:** Be a zero or a Hero. Your choice.

AI-powered cybersecurity competition platform · Cybersecurity Education, Competitive Skill Validation, AI-Assisted Learning, and Gamification · Part of the PRCM™ Labor — COMPASS Career Hub ecosystem

## 1. Project Overview

Cyber Gauntlet Bot is an AI-powered cybersecurity competition platform designed to transform traditional cybersecurity education into an interactive, competitive, and measurable skill-development experience.

The platform operates as a virtual cybersecurity arena called **Red vs Blue: The Hoodie Challenge Arena**, where participants compete by completing realistic cybersecurity challenges, demonstrating technical competency, earning experience points (XP), unlocking achievement badges, and progressing through a structured ranking system.

Unlike conventional learning platforms that primarily measure course completion or theoretical knowledge, Cyber Gauntlet focuses on validating practical cybersecurity skills through hands-on challenges — offensive security exercises, defensive security investigations, technical problem-solving, and collaborative team missions. The evaluation engine assesses submissions, provides contextual feedback, tracks progress, and rewards demonstrated competency, creating a measurable record of skills participants can use to build a portfolio of validated achievements.

**Core objectives:**

- Validate cybersecurity skills through practical challenges.
- Create competitive learning experiences through Red Team and Blue Team exercises.
- Track individual progression using XP, badges, ranks, and performance metrics.
- Encourage consistent participation through daily streaks and milestone rewards.
- Introduce Lean Manufacturing principles into technical skill development.
- Facilitate mentorship between experienced practitioners and developing learners.
- Generate documented achievement records and exportable participant profiles.
- Connect cybersecurity skill validation with the broader PRCM™ Labor ecosystem.

## 2. How the Platform Works

```
Participant Registration (name, username, profile image, classification)
        │
Team Assignment (Red Team: Offensive Security · Blue Team: Defensive Security)
        │
Challenge Assignment & Execution (complete simulated missions, submit evidence)
        │
AI-Assisted Evaluation (technical correctness, relevance, documented methodology)
        │
XP, Badges & Progression (achievements, competition standings, skill records)
        │
Portfolio & Account Export (documented achievements, transferable progress records)
```

Each stage produces information used by subsequent stages — completing a challenge increases XP, updates skill records, contributes to team score, and may unlock a badge or new difficulty tier.

## 3. Participant Registration & Identity Management

Onboarding: introduce the competition, rules, and rewards → collect the participant's name → request a competition username → generate a profile image → establish participant classification → assign to a team → create the initial competition profile.

| Classification | Description |
|---|---|
| Student | Active bootcamp learner with access to competition challenges and student rewards |
| Alumni | Graduated participant who can compete, access advanced challenges, and potentially mentor students |
| Prospect | Potential student exploring the competition through limited demonstration access |

Participant classification is separate from team assignment — an alumnus may be on the Blue Team while a student is on the Red Team.

Example starting profile (illustrative, not a real participant record):

```json
{
  "participant_id": "unique_identifier",
  "real_name": "Participant Name",
  "username": "CyberHero",
  "team": "Blue Team",
  "tier": "Student",
  "level": 1,
  "total_xp": 0,
  "badges": [],
  "completed_challenges": [],
  "current_streak": 0,
  "strike_count": 0
}
```

A standalone application should use unique participant identifiers and secure authentication. Enforcing username uniqueness across all participants requires a shared identity database — a conversation-only GPT cannot reliably guarantee it.

## 4. Red Team vs Blue Team Competition Framework

**🔴 Red Team — "The Breakers"** — offensive security, vulnerability discovery, penetration testing, identifying weaknesses in simulated systems. Categories: web application security and exploitation, network reconnaissance, password/credential security, privilege escalation, social engineering awareness, vulnerability assessment and reporting. *Example mission:* identify a SQL injection vulnerability in an intentionally vulnerable login form, demonstrate the issue within an authorized lab, explain its security impact, and document remediation.

**🔵 Blue Team — "The Guardians"** — defensive security, threat detection, incident response, forensic analysis, protecting simulated infrastructure. Categories: security log analysis, threat hunting, incident response, digital forensics, server/network hardening, security monitoring. *Example mission:* investigate simulated web server logs, identify suspicious activity, classify attack patterns, recommend containment and monitoring improvements.

**Team switching** — participants can request a switch with the `SWAP` command. Eligibility: Level 3+, at least 10 completed challenges on the current team, no strikes in the preceding 30 days, and at least 30 days since the last switch. Approved changes preserve overall XP and badges while resetting team-specific quest progress.

## 5. Cybersecurity Challenge Engine

Each challenge receives an identifier: `[TEAM]_[CATEGORY]_[DIFFICULTY]_[NUMBER]` — e.g. `RED_WEB_BASIC_001`, `BLUE_LOG_INT_001`, `RED_NET_ADV_001`, `LEAN_PROCESS_BONUS_003`.

| Difficulty | XP | Levels | Description |
|---|---|---|---|
| Basic | 100 | 1–2 | Foundational concepts and single-step exercises |
| Intermediate | 250 | 3–4 | Multi-step problems requiring practical application |
| Advanced | 500 | 5–6 | Complex scenarios combining multiple technical skills |
| Expert | 1,000 | 7–10 | Professional-level simulations and multi-stage challenges |

Example challenge record:

```json
{
  "challenge_id": "BLUE_LOG_BASIC_001",
  "title": "Log Analysis Fundamentals",
  "team": "Blue Team",
  "category": "Log Analysis",
  "difficulty": "Basic",
  "base_xp": 100,
  "skills": ["Log Analysis", "Threat Detection", "Incident Response"],
  "objective": "Identify suspicious web server activity",
  "deliverables": ["Suspicious log entries", "Attack classification", "Recommended response actions"]
}
```

**Evaluation outcomes:**

| Submission result | System response |
|---|---|
| Correct and relevant | Full XP and applicable bonuses |
| Partially correct | Partial XP and constructive guidance |
| Incorrect but relevant | No completion XP and educational feedback |
| Off-topic or irrelevant | No XP and a strike under competition rules |

Participants can self-flag uncertain submissions to request guidance without automatically receiving a strike for irrelevance. For a standalone implementation, objective checks and executable tests should be used where possible, with clear rubrics and human review available for disputed results. All offensive exercises should operate exclusively within authorized, isolated training environments.

## 6. XP, Levels, Badges & Gamification

Participants earn XP through challenge completion, bonus objectives, mentorship, team quests, and participation streaks:

| Achievement | XP |
|---|---|
| Lean bonus mission | +50 |
| Speed bonus | +25 |
| Perfect execution | +100 |
| Creative solution | +75 |
| Team quest participation | +150 |
| Mentoring session | +200 |
| Helping a teammate | +50 |

Temporary boosts: an individual boost doubles XP for the next challenge (3 uses/month); a collaborative team boost gives a 1.5× multiplier for 24 hours after a successful team vote.

**Level progression ladder:** Rookie (0–500) → Novice (501–1,500) → Apprentice (1,501–3,500) → Journeyman (3,501–7,000) → Expert (7,001–12,000) → Master (12,001–20,000) → Elite (20,001–35,000) → Champion (35,001–55,000) → Legend (55,001–85,000) → Grandmaster (85,001+).

**Badge categories:** Offensive Security (Lock Picker, Penetration Pro, Web Warrior, Credential Cracker, Privilege Escalator), Defensive Security (Blue Shield, Threat Hunter, Incident Responder, Firewall Master, Forensics Expert), Lean Performance (Efficiency Champion, Value Stream Mapper, Just-In-Time Learner, Kaizen Master, Quality First), Competition Achievements (First Blood, Hot Streak, Century, Champion, Mentor, Veteran, Gauntlet Master). Skill badges progress through Bronze, Silver, Gold, and Platinum tiers.

Daily streaks reward consistency through increasing XP bonuses and milestone badges, with one proactively-activated streak-freeze per 30-day period.

## 7. Lean Manufacturing Integration

| Lean principle | Application |
|---|---|
| Value Stream Mapping | Map challenges to specific technical competencies and identify unnecessary practice |
| Just-In-Time Learning | Present challenges appropriate to the participant's current skill level |
| Kaizen | Encourage continuous improvement through feedback and repeated refinement |
| Pull System | Allow participants to select challenges when ready |
| Quality at Source | Provide immediate feedback and validate understanding before advancement |

## 8. Team Quests, Collaboration & Mentorship

**Team quests** are multi-stage exercises requiring at least three participants, each with distinct responsibilities (e.g. an analyst investigating logs, a responder developing containment measures, an investigator documenting root cause). All required stages must complete before the shared reward is granted.

| Quest tier | Stages | Shared XP pool |
|---|---|---|
| Bronze | 3 | 450 |
| Silver | 5 | 1,000 |
| Gold | 7 | 2,500 |
| Platinum | 10 | 5,000 |

**Purple Team events** combine offensive and defensive perspectives — Red Team participants identify weaknesses while Blue Team participants develop and validate countermeasures, collaborating to improve the training environment's security.

**Mentorship** — eligible alumni and advanced participants can mentor developing learners; matching considers team preference, technical strengths, learning needs, time-zone compatibility, and learning style. Mentors earn XP for qualifying sessions, recorded as part of their competition history.

## 9. Progress Tracking & Participant Analytics

The tracking system defines five per-participant reports: **Hoodie Status Report** (comprehensive profile and achievements), **Activity Log** (timestamped action history), **Badge Sheet** (earned badges and progression requirements), **Strike Log** (violations and resolution history), **Streak Tracker** (daily participation and consistency milestones).

A standalone implementation should generate these reports from a canonical database rather than treating independently edited Markdown files as the authoritative source.

## 10. Competition Integrity & Anti-Cheating

Strike progression: **Strike 1** — warning and explanation; **Strike 2** — warning and reduced XP; **Strike 3** — 24-hour competition cooldown. Strikes clear after 30 days of good standing; participants can self-flag uncertain submissions.

The intended anti-cheating model includes internet restrictions, plagiarism monitoring, timestamped submissions, and participant activity logs — a production application requires explicit technical implementation for these, since a GPT conversation alone cannot guarantee a participant hasn't used external resources or independently verify plagiarism claims. A production system should also include a documented review and appeal process before imposing penalties.

## 11. State Management, Backup & Export

| Export | Purpose |
|---|---|
| HOODIE | Markdown status report with profile image |
| EXPORT STATE | Complete participant state in JSON |
| EXPORT STATE COMPRESSED | Compressed JSON backup |
| EXPORT STATE SUMMARY | Human-readable account summary |
| EXPORT STATE CSV | Structured analytics files |

Import workflow: parse the uploaded JSON → validate schema/version compatibility → check data integrity → identify existing-profile conflicts → resolve via merge/replace/create-new-profile/cancel → restore records → recalculate and display progression.

For production development, XP and achievement history should be verified against trusted records before accepting imported data into competitive leaderboards — otherwise a participant could edit an exported JSON file to award themselves additional XP. The original specification describes a GPT-based, user-controlled export/restore model; it does not establish an existing persistent database or verified cross-session storage. Those would need to be implemented separately for a standalone application.

## 12. Command Interface

| Command | Function |
|---|---|
| `HELP` | Display available commands and competition guidance |
| `MISSION` | Receive a new cybersecurity challenge |
| `SCORE` | View XP, level, team, and progression |
| `PROFILE` | Display the complete participant profile |
| `BADGE` | View or generate achievement badges |
| `HINT` | Request contextual challenge guidance |
| `TEAM` | View team assignments and competition activity |
| `LOG` | Review timestamped participant activity |
| `FEEDBACK` | Record a reflection after completing a challenge |
| `SWAP` | Request a Red Team or Blue Team switch |
| `BOOST` | Activate an available XP multiplier |
| `HOODIE` | Generate the participant status report |
| `EXPORT STATE` | Generate a complete JSON account backup |
| `IMPORT STATE` | Restore a previously exported participant state |
| `BACKUP` | Create a progress checkpoint |

## 13. Proposed Repository Structure

```
cyber-gauntlet-bot/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── .gitignore
├── .env.example
│
├── docs/
│   ├── architecture.md
│   ├── competition-rules.md
│   ├── challenge-guide.md
│   ├── gamification.md
│   ├── data-model.md
│   └── deployment.md
│
├── knowledge-base/
│   ├── cyber_gauntlet_core_system.md
│   ├── cyber_gauntlet_competition_structure.md
│   ├── cyber_gauntlet_gamification_system.md
│   ├── cyber_gauntlet_challenge_library.md
│   ├── cyber_gauntlet_tracking_system.md
│   └── cyber_gauntlet_state_management.md
│
├── frontend/
│   └── src/ (components, pages, hooks, services, assets)
│
├── backend/
│   └── app/ (api, models, services, challenges, evaluation, gamification, tracking, security, exports)
│
├── database/
│   ├── migrations/
│   └── schema.sql
│
├── sandbox/
│   ├── challenge-environments/
│   └── runner/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── security/
│
└── .github/
    ├── workflows/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE.md
```

The `knowledge-base/` directory preserves the six original Cyber Gauntlet operational specification files so contributors can trace application behavior back to the original competition design.

## 14. Proposed Technical Architecture

```
Presentation Layer       web dashboard · chat interface · participant commands
Application Layer        authentication · team management · competition orchestration
Challenge & Evaluation   mission engine · AI feedback · deterministic validation · sandbox runner
Data & Progression       profiles · XP ledger · badges · submissions · audit history
Reporting & Integration  HOODIE exports · JSON backups · analytics · PRCM handoffs
```

| Component | Suggested technology |
|---|---|
| Frontend | React with TypeScript |
| Backend | Python with FastAPI |
| Database | PostgreSQL |
| Data validation | Pydantic |
| AI evaluation | Configurable LLM provider |
| Challenge execution | Isolated, resource-limited containers |
| Background tasks | Celery with Redis |
| Authentication | OpenID Connect-compatible identity provider |
| Testing | Pytest and Playwright |
| CI/CD | GitHub Actions |

The backend should calculate XP and determine level progression itself, rather than relying on the language model to remember totals or calculate rewards consistently — the AI component assists with explanations, contextual hints, and rubric-based feedback while the application maintains authoritative records.

## 15. Proposed Database Design

```
PARTICIPANTS
    ├── TEAM MEMBERSHIP → TEAMS
    ├── CHALLENGE ATTEMPTS → CHALLENGES
    ├── XP TRANSACTIONS
    ├── EARNED BADGES → BADGE DEFINITIONS
    ├── STREAK RECORDS
    ├── STRIKE RECORDS
    ├── REFLECTIONS
    ├── MENTORSHIP RELATIONSHIPS
    └── STATE EXPORTS
```

An XP transaction ledger makes the competition score auditable — rather than merely updating a total, each scoring event creates a transaction that can be inspected, verified, and reversed if necessary.

## 16. Proposed API Design

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/participants` | Register a participant |
| GET | `/api/participants/me` | Retrieve the current profile |
| POST | `/api/teams/join` | Request team assignment |
| GET | `/api/challenges` | Retrieve available missions |
| POST | `/api/challenges/{id}/start` | Start a challenge attempt |
| POST | `/api/attempts/{id}/submit` | Submit a solution |
| GET | `/api/progression/me` | Retrieve XP, badges, and level |
| GET | `/api/leaderboard` | Retrieve competition standings |
| POST | `/api/boosts/activate` | Activate an available boost |
| GET | `/api/exports/hoodie` | Generate a participant report |
| POST | `/api/state/import` | Request state restoration |

Every endpoint that accesses participant data should enforce authentication and authorization; administrators should have separate permissions for reviewing disputes, managing challenges, and approving state changes.

## 17. PRCM™ Labor Ecosystem Integration

```
COMPASS Career Hub (participant routing and context transfer)
        → Cyber Gauntlet (competitive cybersecurity skill validation)
        → GUARDIAN (structured learning)
        → APEX (portfolio and career presentation)
```

Cyber Gauntlet validates technical skills through competition, while other ecosystem tools handle structured learning and career development. Actual cross-tool communication, shared authentication, and automatic data synchronization would require additional integration infrastructure.

## 18. Security, Privacy & Responsible Deployment

- **Challenge isolation** — offensive exercises run in isolated, explicitly authorized environments; participants must not reach production systems or unauthorized external targets.
- **Participant privacy** — real names, activity records, profile images, and histories protected with appropriate access controls; public leaderboards use usernames and configurable visibility.
- **Submission security** — uploaded files/code/responses are untrusted input; execution only within restricted sandboxes with resource limits and monitoring.
- **Competition integrity** — XP, badges, team assignments, and leaderboard updates validated by trusted application logic.
- **State restoration** — imported files schema-validated and checked for tampering before affecting authoritative records.
- **Secrets management** — API keys, database credentials, and auth secrets stay outside the public repository.
- **AI evaluation** — model-generated feedback is not infallible; objective tests, defined rubrics, and human review support important evaluation/disciplinary decisions.

## 19. Development Roadmap

1. **Foundation** — repository, competition rules, participant profiles, team assignment, challenge catalog.
2. **Challenge engine** — challenge assignment, submission handling, technical evaluation, XP calculations, feedback.
3. **Gamification** — levels, badges, streaks, boosts, strike tracking, dashboards.
4. **Competition** — team quests, mentorship coordination, leaderboards, competition events.
5. **Persistence and integration** — full-state restoration, audit logging, reporting, integration interfaces, admin controls.
6. **Production readiness** — automated testing, sandbox hardening, privacy controls, monitoring, deployment docs.

## 20. Repository Source Documentation

The six original Cyber Gauntlet knowledge-base documents serve as the project's functional specifications: `cyber_gauntlet_core_system.md` (mission, philosophy, Lean integration, evaluation framework), `cyber_gauntlet_competition_structure.md` (teams, switching, quests, mentorship, events), `cyber_gauntlet_gamification_system.md` (XP, badges, streaks, leaderboards, boosts, levels), `cyber_gauntlet_challenge_library.md` (mission catalog), `cyber_gauntlet_tracking_system.md` (analytics, logs, reports), `cyber_gauntlet_state_management.md` (exports, restoration, backups, versioning).

These documents describe the intended system but do not, by themselves, constitute a deployed application or an executable codebase.

## License

See [LICENSE](LICENSE).

---

Be a zero or a Hero. Your choice.
