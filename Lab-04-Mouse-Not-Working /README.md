# Lab 4 – Mouse Not Working (Peripheral / Driver Troubleshooting)

> **Lab Type:** Hands-On (VirtualBox)
> This issue was recreated inside a Windows 10 VM by disabling the mouse driver in Device Manager, simulating a real-world "mouse not responding" support ticket, then resolved by re-enabling the correct device.

---

## Quick Summary

| | |
|---|---|
| **Issue Type** | Peripheral / Driver |
| **Reported By** | User (simulated) |
| **Symptom** | Mouse cursor completely unresponsive — no movement on screen |
| **Root Cause** | HID-compliant mouse driver was disabled, so Windows lost the active input connection |
| **Fix** | Re-enabled the HID-compliant mouse device via Device Manager |
| **Status** | Resolved |

## Skills Practiced
- Device Manager Navigation & Driver Management
- Identifying the correct "active" driver among multiple overlapping device entries
- Peripheral / Input Device Troubleshooting
- Root Cause Analysis (RCA)
- Structured Diagnostic Questioning
- Keyboard-Only Navigation (Win + X, Tab, Arrow keys) when the mouse is unavailable
- Incident Documentation & Ticket Writing

---

## Step 1: User Complaint

> "My mouse isn't working. The cursor doesn't move at all on the screen."

### Diagnostic Questions Asked
1. Is your mouse wired or wireless?
2. Does the mouse have a light (optical sensor) turning on underneath?
3. Could you try a different USB port, and test the mouse on another PC/laptop if possible?
4. If it's wireless, is the battery inserted and charged?
5. Have there been any recent Windows updates or driver changes?

### Simulated User Response
> "It's a wired USB mouse. No light turns on underneath at all. I tried a different port, still nothing. It worked fine yesterday, no updates that I know of."

**Key Clues:** - No light at all + different port tested with no change → points toward a driver/detection issue, not a physical fault or bad port

---

## Step 2: Reproducing the Issue (Lab Simulation)

Device Manager showed **three related entries** under "Mice and other pointing devices":
- HID-compliant mouse (×2)
- PS/2 Compatible Mouse

**First attempt:** Disabled **PS/2 Compatible Mouse** → mouse continued working normally.

**Finding:** This confirmed that PS/2 Compatible Mouse was a redundant/legacy driver entry (common in VirtualBox, which emulates a PS/2-style interface), and was **not** the device actually controlling the cursor. This is an important real-world lesson — Device Manager can show multiple overlapping entries for one physical device, and not every entry is "the one in use."

**Second attempt:** Re-enabled PS/2 Compatible Mouse, then disabled a **HID-compliant mouse** entry instead → mouse cursor **stopped moving completely**, confirming this was the correct, active driver.

---

## Step 3: Diagnosis

| Check | Observation |
|---|---|
| Device Manager → Mice and other pointing devices | Multiple entries present (HID-compliant ×2, PS/2 Compatible) |
| Disabling PS/2 Compatible Mouse | No effect — mouse still worked |
| Disabling HID-compliant mouse | Cursor stopped responding entirely |

**Root Cause:** The active HID-compliant mouse driver was disabled, cutting off Windows' connection to the input device. The PS/2 entry present alongside it was a legacy/inactive driver and not responsible for cursor movement in this environment.

---

## Step 4: Navigating Windows Without a Mouse

With the mouse disabled, all navigation was done using the **keyboard only**:

1. Pressed **Win + X** to open the Power User Menu (works entirely via keyboard)
2. Selected **Device Manager** from the menu
3. Used **Tab** and **Arrow keys** to navigate to the disabled HID-compliant mouse entry
4. Opened the context menu and selected **Enable device** **Why this matters:** Just as Lab 3 showed how to navigate Windows with mouse-only when the keyboard fails, this lab demonstrates the reverse — full keyboard-only navigation when the mouse fails. Knowing both directions makes it possible to support a user (or fix your own machine) no matter which input device is down.

---

## Step 5: Fix Applied

1. Re-enabled the correct device — **HID-compliant mouse** — via Device Manager (using keyboard-only navigation)
2. No restart was required

**Result:** Mouse cursor responded immediately after enabling. Verified full functionality by moving the cursor, left-clicking, and right-clicking (tested with a context-menu refresh action).

Full Troubleshooting Evidence (Desktop, Device Manager entries, Disable, Keyboard-only navigation, Re-enable, Verified fix):
![Mouse Lab Evidence](mouse-lab-evidence.png)

---

## Step 6: Alternative Troubleshooting Methods (Reference)

| Option | Method | Best Used When |
|---|---|---|
| **Disable/Enable Device** | Device Manager → Disable, then re-enable the mouse | Safest, least risky fix — used successfully in this lab |
| **Uninstall & Reinstall Driver** | Uninstall device → restart, or Action → Scan for hardware changes | Driver corruption suspected, disable/enable doesn't resolve it |
| **Check Correct Device Entry** | Test each mouse-related entry individually (HID vs PS/2) | Multiple overlapping entries exist, unclear which is active |
| **Physical Port Test** | Move mouse to a different USB port | Ruling out a faulty port before touching software |
| **Battery/Connection Check** | Replace batteries or re-pair (wireless mice) | Wireless mouse with no response at all |

---

## Step 7: Service Desk Ticket Documentation

**Ticket #:** INC001237
**Issue Reported:** User's USB mouse stopped responding completely — no cursor movement on screen.

**Investigation/Findings:** - Confirmed USB port was physically fine (tested a different port)
- Checked Device Manager → found multiple mouse-related entries (HID-compliant ×2, PS/2 Compatible)
- Tested each entry individually to identify which one was actually controlling the cursor
- Found the active **HID-compliant mouse** driver had been disabled

**Root Cause:** The HID-compliant mouse driver — the device actually in use — was disabled, cutting off input to Windows. A separate PS/2 Compatible Mouse entry present in Device Manager was a legacy/inactive driver, unrelated to the issue.

**Resolution:** Re-enabled the HID-compliant mouse device via Device Manager, navigating entirely by keyboard (Win + X → Tab → Arrow keys → Enter). Mouse responded immediately, confirmed working via cursor movement, left-click, and right-click.

**Recommendation:** When multiple mouse-related entries appear in Device Manager, test each individually rather than assuming the first one listed is the active device. Keep a spare USB mouse available for quick swaps during diagnosis if needed.

**Status:** Resolved

---

## Key Learnings
- Device Manager can show **multiple overlapping entries** for a single input device (HID, PS/2, legacy drivers) — not all of them are actually "in use."
- Always **verify which specific driver is active** before concluding a root cause, rather than assuming based on the first entry found.
- **Disable/Enable** is the safest, lowest-risk fix when available — always try it before Uninstall/Reinstall.
- Knowing how to navigate Windows via **keyboard-only** (Win + X, Tab, Arrow keys) is just as valuable as mouse-only navigation — both directions matter in real support work.
- A full fix verification includes testing **movement, left-click, and right-click** — not just "cursor moves."

---

*This lab was completed hands-on inside a Windows 10 VM, simulating a real mouse driver failure and resolving it using standard Service Desk troubleshooting steps.*
