# Customer Journey Map — Add Device (Camera Onboarding)

Source flow: [device-add-flow.md](device-add-flow.md)

## Persona

**Aditya Rao — Security System Installer / Integrator**
JTBD: *"When I'm commissioning or expanding a video surveillance site, I want to add IP cameras into the Device Manager quickly and correctly, so that the system starts recording and monitoring with zero rework or truck rolls."*

- Works on-site, often with intermittent network access and time pressure from the customer.
- Technically competent with networking (IP/MAC, ONVIF) but not a developer — expects clear, guided error recovery.
- Success is measured by the number of devices onboarded per site visit without support escalation.

## Journey Stages

Adapted from the standard funnel to this in-product configuration task (the "purchase" already happened — the job here is successful setup and validation).

| Stage | Description |
|---|---|
| **Trigger (Awareness)** | Installer identifies a new/replacement camera that needs to be added to the system |
| **Preparation (Consideration)** | Gathers device details and decides identification method |
| **Initiation (Acquisition)** | Opens Device Manager and starts the Add Device wizard |
| **Configuration (Onboarding)** | Enters credentials/address, selects node, runs validation |
| **Recovery (Engagement)** | Handles validation errors and retries (if any) |
| **Confirmation (Retention)** | Reviews summary and commits the device registration |
| **Adoption (Advocacy)** | Confirms device is live/associated and moves on to the next device or site |

## Stage-by-Stage Detail

### 1. Trigger — Awareness of need
- **Touchpoints:** Physical camera install, site survey checklist, project handover notes
- **User actions:** Notes device model, mounting location, and network segment
- **Thoughts/questions:** "Do I have the IP/MAC and credentials for this unit?"
- **Emotion:** 🙂 Neutral / task-focused
- **Pain points:** Missing default credentials or IP plan from network team
- **Opportunities:** Pre-populate expected device list from a site survey/import so installer isn't starting from a blank form

### 2. Preparation — Gathering info & choosing method
- **Touchpoints:** Device Manager → Add Device → Add Manually → Device Type = Camera → Identification Method selector
- **User actions:** Chooses **Network Address** (IP/hostname known) or **MAC Address** (device not yet addressed)
- **Thoughts/questions:** "Which method is faster/more reliable for this device?"
- **Emotion:** 🙂 Confident (familiar step)
- **Pain points:** No inline guidance on when to use MAC vs. Network Address; easy to pick wrong path and have to backtrack
- **Opportunities:** Add short contextual help ("Use MAC Address if the camera hasn't been assigned an IP yet") next to the selector

### 3. Initiation — Entering details
- **Touchpoints:** Form fields — IPv4/IPv6/Hostname, Port, Protocol, Username, Password (Network Address) or MAC + credentials (MAC Address)
- **User actions:** Fills form, clicks **Next**, selects the target **Device Node**
- **Thoughts/questions:** "Is this the right node/protocol combination?"
- **Emotion:** 😐 Slight tension — errors here surface later, not immediately
- **Pain points:** No live field validation (e.g., malformed IP, wrong port) until the next step; node list may be long with no search/filter
- **Opportunities:** Inline field validation before "Next"; searchable/grouped node picker

### 4. Configuration & Validation — the moment of truth
- **Touchpoints:** **Test Connection** (ONVIF node) or **Send Onboarding Configuration** (CI node); **Find Device** + network search (MAC Address path)
- **User actions:** Waits for reachability/authentication/ONVIF compatibility check, or device-to-node connection handshake
- **Thoughts/questions:** "Did it find the device? If not, what exactly failed — network, credentials, or compatibility?"
- **Emotion:** 😟 Anxious while waiting → 😃 Relief on success / 😠 Frustration on failure
- **Pain points:** Generic "Display Error" with limited diagnostic detail; unclear whether to retry, change node, or re-check cabling; MAC Address search over the network can be slow with no progress indicator
- **Opportunities:** Differentiate error causes explicitly (unreachable vs. auth failure vs. protocol mismatch) with a suggested next action; show progress/timeout feedback during network discovery

### 5. Recovery — Error handling & retry loop
- **Touchpoints:** Error dialog → return to detail entry (Network Address or MAC Address form)
- **User actions:** Updates address/credentials/port and retries, potentially multiple times
- **Thoughts/questions:** "Is this a typo, a wrong node, or a hardware/network issue?"
- **Emotion:** 😠 Frustration rising with each retry; risk of abandonment after 2–3 failures
- **Pain points:** Form may not retain non-sensitive fields on retry, forcing full re-entry; no escalation path (e.g., "contact network admin") surfaced from the error state
- **Opportunities:** Preserve entered values on retry (except password); add a "Diagnose" or "Get help" link from repeated failures; log failure reason for later support review

### 6. Confirmation — Review & submit
- **Touchpoints:** Review Summary screen → **Add Device**
- **User actions:** Verifies device type, address, node assignment before committing
- **Thoughts/questions:** "Is everything correct before this goes live?"
- **Emotion:** 🙂 Confident (validation already passed)
- **Pain points:** Summary may not surface all entered parameters (e.g., protocol/port), making silent misconfiguration possible
- **Opportunities:** Show a complete, editable summary with an inline "Edit" shortcut back to the relevant step instead of restarting the flow

### 7. Adoption — Registered & associated
- **Touchpoints:** Device Manager list view, live status/health indicator
- **User actions:** Confirms device shows as online/associated with the correct node; moves to next device
- **Thoughts/questions:** "Is it actually streaming/recording, or just 'added'?"
- **Emotion:** 😃 Satisfied / accomplished
- **Pain points:** "Added successfully" doesn't always mean "streaming successfully" — gap between registration and functional confirmation
- **Opportunities:** Auto-show a live thumbnail/health check immediately after "Device Added Successfully" so the installer gets true functional confirmation without navigating away; enable this success to become a repeatable, low-friction pattern for bulk onboarding (advocacy = installer recommends the tool internally for its reliability)

## Critical Moments

- **Aha moment:** Validation succeeds (Test Connection / Send Configuration passes) and the installer sees "Device Added Successfully" with a live indicator — proof the device is truly operational, not just registered.
- **Moments of truth:** The `Validation Successful?` and `Connection Successful?` decision points in both the ONVIF and CI node branches — these determine whether the installer proceeds smoothly or enters a retry loop.
- **Churn/drop-off triggers:** Repeated validation failures with generic error messages (both Network Address and MAC Address paths) are the most likely point installers abandon the flow or escalate to support/truck-roll.

## Journey Map Summary

| Stage | Touchpoint | User Action | Emotion | Pain Point | Opportunity |
|---|---|---|---|---|---|
| Trigger | Site survey / handover | Identify device needing setup | 🙂 Neutral | Missing IP/credential info | Pre-populate device list from survey |
| Preparation | Identification Method selector | Choose Network Address vs. MAC Address | 🙂 Confident | No guidance on which method to use | Contextual help text |
| Initiation | Address/credential form | Enter details, select node | 😐 Slight tension | No inline validation; long node list | Field-level validation, searchable node picker |
| Configuration/Validation | Test Connection / Find Device | Wait for reachability & auth check | 😟→😃/😠 | Generic errors, no progress indicator | Specific error causes, progress feedback |
| Recovery | Error dialog | Correct details and retry | 😠 Frustration | Form doesn't retain values; no help path | Retain non-sensitive fields, add help link |
| Confirmation | Review Summary | Verify and click Add Device | 🙂 Confident | Summary may hide key params | Full editable summary with inline edit |
| Adoption | Device Manager list | Confirm device is live | 😃 Satisfied | "Added" ≠ "streaming" confirmation | Auto-show live thumbnail/health check |

## Prioritized Recommendations

**High impact / quick wins**
1. Replace generic error messages with cause-specific messages (unreachable / auth failure / protocol mismatch) at both `Validation Successful?` decision points.
2. Preserve form field values (except password) when returning to retry after a failed validation.
3. Auto-display a live status/thumbnail check immediately after "Device Added Successfully" to close the registration-vs.-streaming gap.

**Medium impact**
4. Add contextual help distinguishing Network Address vs. MAC Address identification methods.
5. Add a searchable/filterable Device Node picker for sites with many nodes.
6. Expand the Review Summary to show all entered parameters (protocol, port) with inline edit shortcuts.

**Larger investment, high payoff**
7. Support bulk/site-survey-driven device import to remove manual re-entry across many devices.
8. Add a guided diagnostics assistant on repeated validation failure (checks connectivity, credentials, ONVIF compatibility in sequence) to reduce support escalations and truck rolls.
