# Customer Journey Map — Device Auto Discovery (Bulk Camera Onboarding)

Source flow: [device-auto-disc.md](device-auto-disc.md)

> This flow extends the manual add path already mapped in [device-add-flow-customer-journey.md](device-add-flow-customer-journey.md). The **Manual** branch here (Select Camera → Network/MAC Address → ONVIF/CI validation → Review Summary) mirrors that journey almost exactly, so this map focuses on the **Auto Discovery** branch, which introduces a distinct bulk-onboarding experience, and the **shared completion stage** both branches funnel into.

## Persona

**Aditya Rao — Security System Installer / Integrator**
JTBD: *"When I'm commissioning a site with many cameras at once, I want the system to find and let me bulk-add them automatically, so I don't have to manually enter network details for every single device."*

- Handles multi-camera rollouts (10s–100s of devices per site) where manual entry per device is too slow.
- Comfortable choosing scope/node/network parameters, but expects the system to do the heavy lifting of finding and matching devices.
- Success = maximum devices onboarded per discovery run with minimal one-off failures to chase down.

## Journey Stages

| Stage | Description |
|---|---|
| **Trigger (Awareness)** | Multiple new/unregistered cameras exist on the network that need onboarding |
| **Preparation (Consideration)** | Chooses Auto Discovery over Manual; defines scope |
| **Initiation (Acquisition)** | Runs the scan (ONVIF + UPnP) |
| **Processing (Onboarding)** | Reviews merged, de-duplicated results and selects cameras |
| **Configuration (Engagement)** | Assigns node(s) and authenticates/pushes config by integration type |
| **Recovery (Retention)** | Handles partial failures without losing the successful batch |
| **Adoption (Advocacy)** | Devices registered, associated, and available across the platform |

## Stage-by-Stage Detail

### 1. Trigger — Multiple devices need onboarding
- **Touchpoints:** Site rollout plan, network switch/camera inventory
- **User actions:** Recognizes that entering each camera manually would be inefficient
- **Thoughts/questions:** "Can the system find these on its own instead of me typing every IP/MAC?"
- **Emotion:** 🙂 Optimistic — expects a time-saver
- **Pain points:** No way to know upfront how many devices are actually discoverable (ONVIF/UPnP-compliant) before starting
- **Opportunities:** Show an estimated/candidate device count from network scan metadata before committing to full discovery

### 2. Preparation — Choosing Auto Discovery & scope
- **Touchpoints:** Addition Method selector → **Auto Discovery** → Discovery Scope (**All Nodes** / **Specific Node** + optional custom IP range)
- **User actions:** Selects scope; optionally narrows to a node or custom IP range
- **Thoughts/questions:** "Should I scan everything or just this subnet/node to keep results manageable?"
- **Emotion:** 🙂 Confident (clear choice)
- **Pain points:** "All Nodes" scope on large sites can return an overwhelming, hard-to-triage result set; no guidance on when a custom IP range is worth the extra setup
- **Opportunities:** Recommend scoping to Specific Node/IP range when node count exceeds a threshold; remember last-used scope per site

### 3. Initiation — Running the scan
- **Touchpoints:** **Click Search** → parallel **ONVIF Discovery** and **UPnP Discovery**
- **User actions:** Waits for both discovery protocols to complete
- **Thoughts/questions:** "Is this still running, or did it stall?"
- **Emotion:** 😐 Waiting/uncertain — dual-protocol scan has no visible split progress
- **Pain points:** No progress indicator distinguishing ONVIF vs. UPnP scan status; unclear how long a scan "should" take on a large network
- **Opportunities:** Show per-protocol progress and an estimated time remaining; allow canceling a stalled scan without losing prior results

### 4. Processing — Reviewing merged results
- **Touchpoints:** Merge Discovery Results → Remove Duplicate Cameras → Retain Discovery Node Info → **Display Discovered Cameras** → multi-select
- **User actions:** Reviews the deduplicated list, selects one or more cameras to onboard
- **Thoughts/questions:** "Are these really all distinct cameras, or did dedup merge two different units by mistake?"
- **Emotion:** 🙂 Relief that manual entry is avoided, tempered by 😐 uncertainty about list accuracy
- **Pain points:** No visibility into which node found which camera unless explicitly surfaced; dedup logic is a "black box" with no way to review/undo a merge
- **Opportunities:** Show discovery source node per camera in the list; allow expanding/undoing a dedup match if two entries were wrongly merged

### 5. Configuration — Node assignment & integration
- **Touchpoints:** Node Assignment (**Use Discovery Node** vs. **Assign Fixed Node**) → Integration Type (**ONVIF**: enter username/password, authenticate, validate compatibility; **CI**: send integration configuration, camera applies & connects)
- **User actions:** Chooses node assignment strategy, supplies bulk credentials (ONVIF) or triggers bulk config push (CI)
- **Thoughts/questions:** "Do all selected cameras share the same credentials? What happens to the ones that don't?"
- **Emotion:** 😐 Slight tension — bulk actions feel higher-risk than single-device entry
- **Pain points:** A single username/password prompt implies all selected cameras share credentials, which often isn't true across vendors/batches; no per-camera credential override in the flow as drawn
- **Opportunities:** Support per-camera or per-group credential sets before authenticating; preview which cameras will use which node assignment before submitting

### 6. Recovery — Partial failure handling
- **Touchpoints:** `Success?` decision → **Report Failed Cameras** (ONVIF and CI branches)
- **User actions:** Reviews which cameras failed authentication/compatibility/connection while successful ones proceed to registration
- **Thoughts/questions:** "Which specific cameras failed, and why — can I fix and retry just those, without re-running the whole batch?"
- **Emotion:** 🙂 Satisfied for the successful subset → 😠 Frustrated if failed-camera diagnostics are vague or retry requires restarting discovery
- **Pain points:** Flow shows "Report Failed Cameras" as an endpoint with no explicit retry loop back into the batch (unlike Manual, which loops back to re-enter details); risk of having to re-run full discovery just to retry a few failed units
- **Opportunities:** Let the user retry only the failed subset (re-authenticate or reassign node) without repeating discovery; surface a clear per-camera failure reason (auth vs. compatibility vs. network)

### 7. Adoption — Registered across the platform
- **Touchpoints:** **Register Device(s)** → Associate with Selected Node(s) → Add to Platform Inventory → *Available for Monitoring, Recording, Analytics & Events*
- **User actions:** Confirms the successful batch is now active platform-wide
- **Thoughts/questions:** "Are all onboarded cameras actually streaming and feeding analytics, not just listed?"
- **Emotion:** 😃 Accomplished — bulk onboarding completed in one pass
- **Pain points:** Same registration-vs.-functional gap as the manual flow: "added" doesn't confirm live streaming/analytics readiness per camera
- **Opportunities:** Post-onboarding health dashboard showing stream/analytics status per newly added camera, so the installer can confirm the whole batch is truly operational before leaving site

## Critical Moments

- **Aha moment:** The discovered-camera list appears already deduplicated and pre-populated after a single scan — the moment bulk onboarding proves its time savings over manual entry.
- **Moments of truth:** The `Success?` checks after bulk authentication (ONVIF) or configuration push (CI) — determining how much of the batch completes cleanly vs. needs rework.
- **Churn/drop-off triggers:** Partial-failure handling with no batch-scoped retry path is the most likely point installers get frustrated and fall back to onboarding failed units manually one by one, undermining the value of Auto Discovery.

## Journey Map Summary

| Stage | Touchpoint | User Action | Emotion | Pain Point | Opportunity |
|---|---|---|---|---|---|
| Trigger | Site rollout plan | Recognize bulk onboarding need | 🙂 Optimistic | No upfront visibility into discoverable device count | Show candidate device count estimate |
| Preparation | Scope selector | Choose All Nodes / Specific Node / IP range | 🙂 Confident | "All Nodes" can be unmanageable on large sites | Recommend scoping above a device-count threshold |
| Initiation | Search / ONVIF+UPnP scan | Wait for discovery to complete | 😐 Uncertain | No per-protocol progress indicator | Show progress + ETA per protocol |
| Processing | Discovered cameras list | Review & select cameras | 🙂/😐 Relief with doubt | Dedup logic is a black box | Show source node per camera; allow undoing merges |
| Configuration | Node assignment + credentials | Assign nodes, authenticate/push config | 😐 Tension | Single credential set assumed for all cameras | Support per-camera/group credentials |
| Recovery | Report Failed Cameras | Review batch failures | 😃/😠 Mixed | No batch-scoped retry; may need to restart discovery | Retry only failed subset in place |
| Adoption | Platform inventory | Confirm devices are live | 😃 Accomplished | "Registered" ≠ confirmed streaming/analytics | Post-onboarding health dashboard per camera |

## Prioritized Recommendations

**High impact / quick wins**
1. Add a batch-scoped retry for **Report Failed Cameras** so installers fix and retry only the failed subset instead of re-running full discovery.
2. Surface per-camera failure reason (auth vs. compatibility vs. network) at the `Success?` decision points.
3. Show per-protocol (ONVIF/UPnP) scan progress instead of a single opaque "searching" state.

**Medium impact**
4. Display the discovery source node per camera in the results list, with the ability to review/undo a duplicate merge.
5. Support per-camera or per-group credentials during bulk ONVIF authentication instead of a single shared prompt.
6. Recommend narrowing scope (Specific Node/IP range) when "All Nodes" would return an unmanageably large result set.

**Larger investment, high payoff**
7. Post-onboarding health dashboard showing live stream/analytics status per newly onboarded camera, closing the registration-vs.-functional confirmation gap for the whole batch.
8. Estimate discoverable device count before running a full scan, using cached network/node metadata, to set expectations for large rollouts.
