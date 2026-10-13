# Microsoft Sentinel — Automation Rules

## Objective

Configure Microsoft Sentinel automation rules to automate incident triage, assignment, escalation, and response actions.

---

## 1. High-Severity Incident Assignment

### Rule Configuration

* **Rule name:** `AR-High-Severity-Incident-Assignment`
* **Trigger condition:** When incident is created
* **Incident conditions:** Severity equals `High`
* **Actions:**

  * Assign incident to SOC Tier-2 analyst/team
  * Add `High-Severity` tag

![High-severity automation rule](screenshots/automation-rules/01-high-severity.png)

### Result

High-severity incidents are automatically assigned for Tier-2 investigation.

---

## 2. Critical Incident Escalation

### Rule Configuration

* **Rule name:** `AR-Critical-Incident-Escalation`
* **Trigger condition:** When incident is created
* **Incident conditions:** Severity equals `Critical`
* **Actions:**

  * Assign incident to SOC Tier-2
  * Add `Critical` tag
  * Run escalation playbook

![Critical incident automation](screenshots/automation-rules/02-critical-escalation.png)

### Result

Critical incidents are automatically escalated for further investigation.

---

## 3. Brute-Force Investigation

### Rule Configuration

* **Rule name:** `AR-Brute-Force-Investigation`
* **Trigger condition:** When incident is created
* **Incident conditions:** Analytics rule name contains `Brute Force`
* **Actions:**

  * Add `BruteForce` tag
  * Assign incident to identity/security analyst
  * Add investigation tasks

![Brute-force automation rule](screenshots/automation-rules/03-brute-force.png)

### Result

Brute-force incidents are automatically identified and routed for identity-focused investigation.

---

## 4. Suspicious Sign-In Triage

### Rule Configuration

* **Rule name:** `AR-Suspicious-SignIn-Triage`
* **Trigger condition:** When incident is created
* **Incident conditions:** Analytics rule name contains `Suspicious Sign-In`
* **Actions:**

  * Add `Identity` tag
  * Assign incident to identity analyst
  * Add investigation task

![Suspicious sign-in automation](screenshots/automation-rules/04-suspicious-signin.png)

### Result

Suspicious authentication incidents are automatically categorized and assigned for investigation.

---

## 5. Malware Incident Response

### Rule Configuration

* **Rule name:** `AR-Malware-Incident-Response`
* **Trigger condition:** When incident is created
* **Incident conditions:** Analytics rule name contains `Malware`
* **Actions:**

  * Add `Malware` tag
  * Assign incident to endpoint analyst
  * Run response playbook

![Malware automation rule](screenshots/automation-rules/05-malware.png)

### Result

Malware-related incidents are automatically routed to endpoint investigation and response.

---

## 6. Standard Investigation Tasks

### Rule Configuration

* **Rule name:** `AR-Standard-Investigation-Tasks`
* **Trigger condition:** When incident is created
* **Incident conditions:** Severity equals `Medium` or `High`
* **Actions:**

  * Add investigation task
  * Review incident timeline
  * Review related alerts
  * Investigate entities
  * Document findings

![Investigation task automation](screenshots/automation-rules/06-investigation-tasks.png)

### Result

Standard investigation tasks are automatically added to qualifying incidents.

---

## 7. Known Activity Suppression

### Rule Configuration

* **Rule name:** `AR-Known-Activity-Suppression`
* **Trigger condition:** When incident is created
* **Incident conditions:** Incident matches a documented known-noise detection
* **Actions:**

  * Close incident
  * Set appropriate closing reason
  * Add investigation comment

![Known activity automation](screenshots/automation-rules/07-known-activity.png)

### Result

Documented false-positive or known-noise incidents are automatically handled without unnecessary analyst investigation.

---

## 8. Identity Incident Routing

### Rule Configuration

* **Rule name:** `AR-Identity-Incident-Routing`
* **Trigger condition:** When incident is created
* **Incident conditions:** Incident matches an identity-related analytics rule
* **Actions:**

  * Assign incident to identity/security analyst
  * Add `Identity` tag

![Identity routing automation](screenshots/automation-rules/08-identity-routing.png)

### Result

Identity-related incidents are automatically routed to the appropriate investigation team.

---

## 9. High-Severity Status Automation

### Rule Configuration

* **Rule name:** `AR-High-Severity-Status`
* **Trigger condition:** When incident is created
* **Incident conditions:** Severity equals `High`
* **Actions:**

  * Change status to `Active`
  * Assign incident owner
  * Add `Priority-Investigation` tag

![Status automation rule](screenshots/automation-rules/09-status-automation.png)

### Result

High-severity incidents are automatically moved into an active investigation state.

---

## 10. Incident Escalation

### Rule Configuration

* **Rule name:** `AR-Incident-Escalation`
* **Trigger condition:** When incident is updated
* **Incident conditions:** Severity changes to `High` or `Critical`
* **Actions:**

  * Assign incident to SOC Tier-2
  * Add `Escalated` tag
  * Run escalation playbook

![Incident escalation automation](screenshots/automation-rules/10-escalation.png)

### Result

Incidents that increase in severity are automatically escalated for additional investigation.

---

## Validation

* [ ] Automation rules created
* [ ] Trigger conditions configured
* [ ] Incident conditions configured
* [ ] Actions configured
* [ ] Rules enabled
* [ ] Test incidents generated
* [ ] Automated actions verified
* [ ] Screenshots captured

## Result

Microsoft Sentinel automation rules were configured to automate incident assignment, categorization, investigation tasks, escalation, and response actions.
