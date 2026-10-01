# Microsoft Sentinel — Workbooks

## Objective

Create and use Microsoft Sentinel workbooks to visualize security data and support investigation.

## 1. Open Workbooks

Navigate to:

`Microsoft Sentinel → Content Hub → Workbooks`

Review the available workbook templates.

![Sentinel workbooks](screenshots/workbooks/01-workbooks.png)

## 2. Deploy a Workbook

Select a relevant workbook template and choose **Save** or **Create**.

Configure:

* Subscription
* Resource group
* Log Analytics workspace
* Workbook name

![Workbook configuration](screenshots/workbooks/02-workbook-config.png)

## 3. Review Workbook

Open the deployed workbook and review the available security visualizations.

Review metrics such as:

* Authentication activity
* Sign-in failures
* Security events
* Alert activity
* Geographic activity

![Workbook dashboard](screenshots/workbooks/03-workbook-dashboard.png)

## 4. Query Workbook Data

Review the underlying queries used by the workbook to understand how the visualizations are generated from Log Analytics data.

![Workbook query](screenshots/workbooks/04-workbook-query.png)

## Validation

* [ ] Workbook template reviewed
* [ ] Workbook deployed
* [ ] Log Analytics workspace configured
* [ ] Workbook opened successfully
* [ ] Security visualizations reviewed
* [ ] Underlying queries reviewed

## Result

A Microsoft Sentinel workbook was deployed and used to visualize security telemetry from the Log Analytics workspace. The underlying queries were reviewed to understand how the visualizations are generated.
