# Microsoft Sentinel — Automation

## Objective

Automate Sentinel incident response actions using automation rules and playbooks.

## 1. Create Automation Rule

Navigate to:

`Microsoft Sentinel → Automation`

Create an automation rule for the required incident condition.

Configure:

* Rule name
* Trigger condition
* Incident conditions
* Actions

![Automation rule](screenshots/automation/01-automation-rule.png)

## 2. Configure Incident Action

Configure the automation rule to perform an action when the specified incident condition is met.

Example actions:

* Assign incident owner
* Change incident status
* Add incident tags
* Run a playbook

![Automation action](screenshots/automation/02-automation-action.png)

## 3. Configure Playbook

If a playbook is required, create or select an Azure Logic App and configure it as the automated response.

![Playbook configuration](screenshots/automation/03-playbook.png)

## 4. Validate Automation

Generate or use a test incident that matches the automation rule conditions.

Verify that the configured action executes successfully.

![Automation result](screenshots/automation/04-automation-result.png)

## Validation

* [ ] Automation rule created
* [ ] Trigger conditions configured
* [ ] Incident action configured
* [ ] Playbook configured when required
* [ ] Automation tested
* [ ] Automated action verified

## Result

Microsoft Sentinel automation was configured to perform a defined response action when matching incident conditions were detected.
