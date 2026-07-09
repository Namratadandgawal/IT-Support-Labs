# Lab 2 – PC Won't Turn On (Hardware Troubleshooting)

> **Lab Type:** Simulated Scenario (Role-Play)
> Hardware power failures cannot be recreated inside a virtual machine, so this lab was conducted as a structured role-play exercise, following the exact questioning order, safety steps, and diagnostic logic used in real Desktop Support tickets.

---

## 📋 Quick Summary

| | |
|---|---|
| **Issue Type** | Hardware / Power |
| **Reported By** | User (simulated) |
| **Symptom** | PC shows zero response — no lights, no fan, no sound |
| **Root Cause** | RAM stick not fully seated, dislodged during cabinet cleaning |
| **Fix** | Removed and firmly reseated the RAM stick |
| **Status** | ✅ Resolved |

## 🛠 Skills Practiced
- Hardware Troubleshooting
- Structured Diagnostic Questioning
- Root Cause Analysis (RCA)
- Power Supply Chain Checking (socket → cable → strip → internal)
- PC Safety Procedures (ESD / anti-static handling)
- Incident Documentation & Ticket Writing

---

## 🗣️ Step 1: User Complaint

> "My desktop computer won't turn on at all. I pressed the power button, but nothing happens no lights, no sound, nothing."

### Diagnostic Questions Asked
1. Could you please check if all the cables (power cable, monitor cable) are properly connected?
2. When you press the power button, do you notice any lights, fan sounds, or beep sounds?
3. Is this problem only with your PC, or are other computers in the same room/office also affected?
4. Has this happened before, or is this the first time?
5. Was there any recent power cut, thunderstorm, or was the PC moved/cleaned recently?

### User's Response
> "I checked the power cable, it's connected properly. When I press the power button, there's no light, no fan sound, nothing at all. Only my PC has this issue, others are working fine. This never happened before. No power cut recently, but I did clean my PC (opened the cabinet and cleaned dust) two days ago."

**🔑 Key Clues:**
- Zero power response (no lights/fan) → points to a power-chain or connection issue, not software
- Cabinet was opened for cleaning 2 days ago → strong hint something got physically disturbed

---

## 🔍 Step 2: Structured Hardware Check

Hardware issues are always checked in order — **simplest/external first, complex/internal last** to avoid wasting time opening the cabinet unnecessarily.

| Step | Check | Method | Result |
|---|---|---|---|
| 1 | Wall socket | Tested with a phone charger | ✅ Socket has power |
| 2 | Power cable | Tried a spare/different cable | ❌ Still no response |
| 3 | Power strip | Bypassed strip, plugged directly into wall | ❌ Still no response |
| 4 | Internal check | Opened the cabinet | 🔍 Found the issue |

---

## ⚠️ Step 3: Safety Precautions (Before Opening the Cabinet)

Two non-negotiable safety steps before touching any internal components:

1. **Unplug the power cable completely** — prevents electric shock or short-circuiting
2. **Discharge static electricity** — touch a grounded metal surface (e.g., the PC chassis) or use an anti-static wrist strap before touching RAM/motherboard, to prevent ESD (Electrostatic Discharge) damage

---

## 🧩 Step 4: Internal Inspection & Root Cause

| Component Checked | Status |
|---|---|
| 24-pin power cable (PSU → motherboard) | ✅ Firmly connected |
| RAM stick seating | ❌ Loosely seated, not fully pushed in |
| Front panel power switch cable | ✅ Properly connected |

**Root Cause:**
The RAM stick was not fully seated in its slot most likely dislodged while the user was cleaning the cabinet two days earlier. Many motherboards will not begin the power-on sequence at all if RAM isn't making a full connection, which explains the complete absence of lights or fan sound.

---

## ✅ Step 5: Fix Applied

1. Removed the RAM stick completely
2. Cleaned the RAM slot of dust
3. Firmly reseated the RAM stick until both side clips clicked into place
4. Reconnected all cables and powered on the PC

**Result:** PC powered on normally — lights, fan sound, and boot sequence confirmed working.

---

## 🎫 Step 6: Service Desk Ticket Documentation

**Ticket #:** INC001235
**Issue Reported:** Desktop PC would not turn on — no lights, no fan sound, no response on power button press.

**Investigation/Findings:**
- Wall socket confirmed working (tested with phone charger)
- Different power cable tested — no change
- Power strip bypassed — no change
- Cabinet opened (after unplugging + anti-static precaution) — RAM found loosely seated

**Root Cause:** RAM stick not properly seated, likely dislodged during recent cabinet cleaning, blocking the motherboard's power-on sequence.

**Resolution:** Removed and firmly reseated the RAM stick until fully clicked in. PC powered on successfully afterward.

**Recommendation:** Advise user to power off and unplug the PC before cleaning, avoid touching internal components directly, and ensure all connections are firm before closing the cabinet.

**Status:** ✅ Resolved

---

## 🎓 Key Learnings
- Hardware checks should always go **external/simple → internal/complex** (socket → cable → strip → cabinet)
- "Plugged in" ≠ "confirmed working" — always test, don't just visually inspect
- **Safety first:** always unplug power and discharge static electricity before touching internal components
- A loose RAM stick can cause a PC to show **zero signs of power** — a motherboard protection behavior, not necessarily a fault
- Recent physical changes (like cleaning) are often the strongest clue toward root cause
- Clear ticket documentation (Issue → Investigation → Root Cause → Resolution → Recommendation) builds trust and prevents reopened tickets

---

*This lab was completed as a simulated hands-on IT Desktop Support scenario, following real-world troubleshooting logic from user complaint to resolution.*
