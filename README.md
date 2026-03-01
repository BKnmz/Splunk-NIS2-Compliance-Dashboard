# 🛡️ Splunk NIS-2 Compliance Monitoring Dashboard

## 📌 Objective
As a Security Compliance Analyst / Product Owner, I developed an automated Splunk dashboard to monitor Security Operations Center (SOC) incident response times against the strict regulatory SLAs defined by the **NIS-2 Directive (Article 23)**. 

Under NIS-2, organizations must submit an "Early Warning" within 24 hours of a significant incident and a "Full Report" within 72 hours. Failure to meet these deadlines can result in massive regulatory fines.

## 🛠️ Tools & Technologies
* **Platform:** Splunk Cloud
* **Language:** Search Processing Language (SPL)
* **Framework:** NIS-2 Directive, Risk Management, SLA Tracking

## 📊 The Dashboard Overview
![Splunk Dashboard Screenshot]() 
*(Note: Ensure your uploaded screenshot is named dashboard.png for this image to show up!)*

## 🔍 Key Compliance Metrics Tracked (SPL Queries)

### 1. 🚨 URGENT: 24-Hour Early Warning Breaches
Identifies incidents that have surpassed the 24-hour mark without an Early Warning submission.

``source="nis2_incidents.csv" severity="Significant" hours_since_detection > 24 regulatory_status="Investigating" | table incident_id, hours_since_detection, system_impacted``

### 2. ⚠️ Approaching 72-Hour Full Report Deadline
Highlights incidents where an Early Warning was submitted, but the 72-hour final report deadline is approaching.
``source="nis2_incidents.csv" severity="Significant" hours_since_detection > 48 regulatory_status="Early Warning Submitted" | table incident_id, hours_since_detection, system_impacted``

###3. 📈 Reporting Status Distribution
Provides a high-level overview for the CISO and Compliance Officers regarding the current status of all significant incidents.

``source="nis2_incidents.csv" severity="Significant" | stats count by regulatory_status``

##💡 Business Value
This dashboard transitions compliance from a reactive, manual audit process into a proactive monitoring system.
By providing real-time visibility into SLA timelines, the Product Owner can ensure the SOC is operating within legal boundaries, drastically reducing the risk of regulatory penalties.
