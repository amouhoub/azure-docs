---
title: Explore the new Alerts experience in Azure Monitor| Microsoft Docs
description: Understand how the new simple and scalable alerts experience in Azure makes authoring, viewing and managing alerts easier
author: manishsm-msft
manager: kmadnani1
editor: ''
services: monitoring-and-diagnostics
documentationcenter: monitoring-and-diagnostics

ms.assetid:
ms.service: monitoring-and-diagnostics
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/23/2018
ms.author: mamit
ms.custom:

---
# The new alerts experience in Azure Monitor

## Overview
Alerts has new experience. The older alerts experience is now under the Alerts (Classic) tab. The new Alerts experience has the following benefits over the Alerts (Classic) experience:

 - **Separation of Fired alerts and Alert Rules** - Alert Rules (the definition of condition that triggers an alert), and Fired Alerts (an instance of the alert rule firing) are differentiated, so the operational and configuration views are separated.
 - **A unified authoring experience**  - All alert creation for metrics, logs and activity log across Azure Monitor, Log Analytics, and Application Insights is in one place. 
 - **View fired Log Analytics alerts in Azure portal** - You can now also see fired Log Analytics alerts in your subscription. Previously these were in a separate portal. 
 - **Better workflow** - The new alerts authoring experience guides the user along the process of configuring an alert rule, which makes it simpler to discover the right things to get alerted on.
 

The following sections describe, in more detail, how the new experience works.

## Alert rules terminology
The new alerts experience uses the following concepts to separate the Alert Rule and Fired Alert objects while unifying the authoring experience across different alert types.

- **Target Resource** - A target can be any Azure resource. Target Resource defines the scope and signals available for alerting. Example targets: a virtual machine, a storage account, a virtual machine scale set, a Log Analytics workspace, or an Application Insights resource.

- **Criteria** - Criteria is combination of Signal and Logic applied on a Target resource. Examples: Percentage CPU > 70%, Server Response Time > 4 ms, Result count of a log query > 100 etc. 

- **Signal** - Signals are emitted by the Target resource and can be of several types. **Metric**, **Activity log**, **Application Insights**, and **Log** are supported Signal types.

- **Logic** - User-defined logic to check if the Signal is within expected range/values.  
 
- **Action** - A specific action taken when the alert is fired. For example, emailing an email address or calling a webhook URL. Multiple actions may occur when an alert fires. These alerts support action groups.  
 
- **Alert rule** - The condition that would trigger the alert. The alert rule captures the Target and Criteria for alerting. The Alert rule can be in an Enabled or a Disabled state.
 
    > [!NOTE]
    > This is different from Alerts (Classic) experience where the alert represents both the rule and fired alert and therefore can be in one of Warning, Active or Disabled states.
    >

## Single place to view and manage alerts
The goal of the Alerts experience is to be the single place to view and manage all your Azure alerts. The following subsections describe the functions of each individual screen of the new experience.

### Alerts overview page
**Monitor - Alerts** overview page shows aggregated summary of all the fired alerts, and total configured/enabled alert rules. It also shows a list of all fired alerts. Changing the subscriptions or filter parameters updates the aggregates and the alerts fired list.

> [!NOTE]
> Fired Alerts shown in Alerts are limited to supported metric and activity log alerts; Azure Monitor Overview shows count of fired alerts including those in older Azure Alerts

 ![alerts-overview](./media/monitoring-overview-unified-alerts/alerts-preview-overview2.png) 

### Alert rules management
**Monitor - Alerts>Rules** is a single page to manage all alert rules across your Azure subscriptions. It lists all the alert rules (enabled or disabled) and can be sorted based on target resources, resource groups, rule name, or status. Alert rules can also be disabled/enabled or edited from this page.  

 ![alerts-rules](./media/monitoring-overview-unified-alerts/alerts-preview-rules.png)


## One alert authoring experience across all monitoring sources
In the new Alerts experience, alerts can be authored in a consistent manner regardless of the monitoring service or signal type. All alerts fired and related details are available in single page.  
 
Authoring an alert is a three-step task where the user first picks a target for the alert, followed by selecting the right signal and then specifying the logic to be applied on the signal as part of the alert rule. This simplified authoring process no longer requires the user to know the monitoring source or signals supported before selecting an Azure resource. The common authoring experience automatically filters the list of available signals based on target resource selected and guides the creation of alert logic

You can learn more on how to create following alert types [here](monitor-alerts-unified-usage.md).
- Metric Alerts
- Log alerts (Log Analytics)
- Log alerts (Activity Logs)
- Log alerts (Application Insights)

 

## Alert types supported


| **Signal Type** | **Monitor Source** | **Description** | 
|-------------|----------------|-------------|
| Metric | Azure monitor | Also called [**Near-Real-Time Metric alerts**](monitoring-near-real-time-metric-alerts.md), these metric alerts support evaluating metric conditions as frequently as 1 min and allow for multi-metric rules. A list of supported resource types is available [here](monitoring-near-real-time-metric-alerts.md#metrics-and-dimensions-supported). Older metric alerts as defined [here](monitoring-overview-alerts.md#alerts-in-different-azure-services) are not supported in the new Alerts experience. You can find them under Alerts (Classic)|
| Logs  | Log Analytics | Receive notifications or run automated actions when a Log search query over metric and/or event data meets certain criteria.|
| Activity Log | Activity Logs | This category contains the records of all Create, Update, and Delete actions performed through the selected target (resource/resource group/subscription). |
| Logs  | Service Health Logs | Not supported in Alerts experience.   |
| Logs  | Application Insights | This category contains logs with the performance details of your application. Using analytics query, you can define the conditions for the actions to be taken - based on the application data. |
| Metric | Application Insights | Not supported in Alerts experience. You will find them under Alerts (Classic) |
| Availability Tests | Application Insights | Not supported in Alerts experience. You will find them under Alerts (Classic) |


## Next steps
- [Learn how to use the new Alerts experience to create, view, and manage alerts](monitor-alerts-unified-usage.md)
- [Learn about log alerts in Alerts experience](monitor-alerts-unified-log.md)
- [Learn about metric alerts in Alerts experience](monitoring-near-real-time-metric-alerts.md)
- [Learn about Activity log alerts in Alerts experience](monitoring-activity-log-alerts-new-experience.md)
