# ServiceNow_ITOM_Project5
ServiceNow ITOM Project 5 – AIOps Event to Incident Automation
# 🚀 ServiceNow ITOM Project 5 – AIOps Event to Incident Automation (Flow Designer Simulation)

**Author:** Srikanth Madabhushi  
**Platform:** ServiceNow Yokohama PDI  
**Domain:** IT Operations Management (ITOM)  
**Focus:** AIOps | Event Management | Predictive Automation | CMDB Integration  

---

## 🧠 Project Overview
This project demonstrates **AI-Driven Event Management automation** using **ServiceNow Flow Designer**.  
The system intelligently converts incoming **Event Ingestion records** into actionable **Incidents**, linking each record to its **Configuration Item (CI)** within the CMDB.

This simulation mirrors real-world **AIOps event correlation**, where alerts from tools like **Splunk, Dynatrace, or Datadog** are automatically transformed into ServiceNow incidents.

---

## 🎯 Objectives
- Automate event-to-incident conversion.
- Correlate each event with the right **Configuration Item (CMDB CI)**.
- Use **Flow Designer** to dynamically apply logic based on event severity.
- Maintain clean logs for every flow execution.
- Demonstrate intelligent prioritization for AIOps Support scenarios.

---

## 🧩 Architecture & Flow
1. **Event Ingestion Table (`u_event_ingestion`)** receives events from monitoring tools.
2. **Flow Designer** triggers when a new record is created.
3. If **Severity ≥ 3**, the flow:
   - Creates an **Incident**.
   - Populates `Short description`, `Description`, `Priority`, `Impact`, `Urgency`, and `CMDB CI`.
   - Adds detailed **Work Notes**.
4. If **Severity < 3**, the flow logs the event and skips incident creation.
5. All actions are captured in **Flow Executions** and **System Logs**.

---

## 🧱 CMDB Setup
| CI Name | Type | Environment | Region |
|----------|------|-------------|--------|
| Server_101 | Computer | Production | US |
| Server_202 | Computer | Production | EU |
| Server_303 | Computer | Test | APAC |

---

## 🧰 Flow Designer Actions
| Step | Action | Description |
|------|---------|-------------|
| 1 | **Trigger: Record Created** | When a new Event Ingestion record is created. |
| 2 | **If Condition** | Severity ≥ 3 |
| 3 | **Create Incident** | Auto-creates an Incident with populated CI and fields. |
| 4 | **Update Record** | Adds detailed work notes. |
| 5 | **Log Message** | Logs skipped low-severity events. |

---

## ⚙️ Field Mapping
| Event Field | Incident Field |
|--------------|----------------|
| `metric_name` | Short Description |
| `metric_value` | Description |
| `severity` | Priority / Urgency |
| `ci` | CMDB CI |
| `region` | Description |
| `source` | Work Notes |

---

## 🧪 Testing Steps
1. Navigate to **Event Ingestion → New**.
2. Add an event:
   - Source: Splunk  
   - Metric: CPU_Usage  
   - Value: 95  
   - Severity: 5  
   - CI: Server_101  
3. Submit the record.
4. Navigate to **Incidents → All**.
5. Verify:
   - New incident created.  
   - CMDB CI populated.  
   - Priority = 1 (Critical).  
   - Work Notes logged correctly.

---

## 📊 Flow Diagram
*(Include your downloaded flow diagram PNG here)*  
`/Diagrams/Flow_Diagram.png`

---

## 🌱 Future Enhancements
- Integrate with **Predictive Intelligence** for automated root cause analysis.
- Extend for **Change Management** risk scoring.
- Include **Service Mapping** and **Event Correlation Rules**.
- Integrate **Snowflake/JIRA** for cross-platform tracking.

---

## 🧠 Learning Outcome
This project deepens practical knowledge of:
- CMDB and CI dependencies.
- Event correlation & AIOps in ITOM.
- Flow Designer automation design.
- Impact/Urgency/Priority logic.
- Log tracking and troubleshooting.

---

## 🏁 References
- [ServiceNow ITOM Documentation](https://docs.servicenow.com)
- [Predictive Intelligence Overview](https://docs.servicenow.com/bundle/utah-now-intelligence/page/use/predictive-intelligence/concept/predictive-intelligence.html)
- [AIOps Event Management](https://docs.servicenow.com/bundle/utah-it-operations-management/page/product/event-management/concept/aiops-overview.html)

---

📂 **Repository:** [github.com/srikanthmadabhushi/ServiceNow_ITOM_Project5](https://github.com/srikanthmadabhushi/ServiceNow_ITOM_Project5)
