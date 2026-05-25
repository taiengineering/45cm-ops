# System Status Handoff — 2026-05-25

## 1. Federation / Runtime Separation

### Completed
- 45cm-mkt runtime recovered from long FAILED state.
- Railway 9/9 SUCCESS verified.
- Marketing runtime physically separated.
- Canonical ownership moved to `45cminc/mkt-runtime`.
- Legacy repos frozen and isolated.
- Federation governance consolidated.

### Current Canonical Runtime Ownership
| Runtime | Repo |
|---|---|
| MKT | 45cminc/mkt-runtime |
| OPS | taiengineering/45cm-ops |
| FGW | taiengineering/FGW-v3 |
| TAI API | taiengineering/tai-api |

---

## 2. Capability Asset Extraction

### Final Frozen Capability Assets

#### Standalone
- slack
- fcm
- sms
- mail
- biz-verify

#### Adapter-based
- upload
- oauth
- audit
- auth(core only)

### Asset Rules
- No FastAPI dependency in core
- No direct DB access in core
- Adapter boundary mandatory
- Copy-ready structure fixed
- Service rewrite stopped

### Explicitly Deferred
- CRM
- Payment runtime
- Workflow platform
- Giant auth runtime
- Orchestration systems

---

## 3. Wrapper Migration Status

### Completed
| Phase | Status |
|---|---|
| Phase 1 | DONE |
| Phase 2 | DONE |

### Migrated Routers
- roles.py
- uploads.py
- biz_verify.py
- messaging.py
- fcm.py

### Migration STOP
Phase 3-4 intentionally frozen.
Current objective achieved: reusable capability extraction.

---

## 4. OPS Observation Pipeline

### Completed
- `observation_results` table created.
- `runtime_sources` table created.
- OPS persistence added.
- SAFE runtime added to source registry.
- FGW observation endpoint added.
- Runtime source CRUD API added.
- Runtime source UI added.

### Verified Runtime Observation
| Runtime |
|---|
| tai |
| safe |
| mkt |
| fgw |

### Current Signal Flow
runtime health
→ OPS observe
→ persistObservation()
→ Supabase observation_results
→ FGW federation
→ UI consume

---

## 5. OPS Service Status (IMPORTANT)

### What Is COMPLETE
- Runtime observation
- Runtime persistence
- Runtime projection
- Basic runtime UI
- Runtime source management UI

### What Is NOT COMPLETE
- Incident system
- Alert system
- Timeline/history
- Service-level operational dashboard
- ADMIN onboarding
- APP onboarding
- Detailed health checks

### Current Highest Priority
#### P0
OPS dynamic registry stabilization.

Current issue:
- runtime_sources CRUD exists
- UI exists
- OPS dynamic consume build failed
- UI → OPS automatic observation not fully stabilized yet

---

## 6. Current OPS Direction (IMPORTANT)

OPS is NOT:
- orchestration platform
- runtime control plane
- deployment manager
- service mesh

OPS IS:
- service observation system
- runtime truth projection system
- operational visibility layer

---

## 7. Remaining Real Operational Work

### P0
- Fix OPS dynamic registry async build failure.
- Verify UI-added runtime source automatically becomes observable.

### P1
Onboard real operational services:
- ADMIN
- APP

### P2
Add service-specific deep health checks.

Examples:
#### TAI
- DB
- queue
- AI
- storage

#### SAFE
- websocket
- watch loop
- alert dispatch

#### ADMIN
- login
- auth
- dashboard API

#### APP
- push
- websocket
- realtime

### P3
Incident system.

### P4
Alert system.

### P5
Operational dashboard.

---

## 8. Most Important Final Decision

Capability extraction is COMPLETE.

The system will NOT move toward:
- giant capability platform
- orchestration runtime
- capability graph
- service decomposition obsession

The architecture direction is now:
- small reusable capability assets
- copy-ready behavior blocks
- service-owned domain/state
- capability-owned execution behavior only

---

## Final Principle

Capability does not replace services.
Capability only makes repeated behavior reusable.

OPS does not control services.
OPS observes and projects operational truth.
