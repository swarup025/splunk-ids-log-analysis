# splunk-ids-log-analysis
🔐 IDS Log Analysis & SOC Monitoring Using Splunk
📌 Project Overview

This project demonstrates Intrusion Detection System (IDS) log analysis, monitoring, and threat visualization using Suricata and Splunk in a simulated Security Operations Center (SOC) environment.
The primary objective of this project is to analyze raw IDS alerts, detect suspicious activity, and build security dashboards that support real-world SOC Level-1 monitoring workflows.

🎯 Project Objectives

Collect and ingest Suricata IDS logs into Splunk
Analyze intrusion alerts and suspicious traffic
Write custom SPL queries for threat detection
Identify attack patterns (scanning, brute-force, unusual traffic)
Perform severity-based alert triage
Design SOC-style monitoring dashboards
Simulate L1 SOC investigation workflow

🛠️ Tools & Technologies Used

IDS: Suricata
SIEM: Splunk
Query Language: SPL (Search Processing Language)
Operating System: Kali Linux / Linux
Dataset: Botsv2 (Splunk Lab Dataset)

🏗️ Project Architecture

Attacker Traffic (Simulated)
        ↓
Suricata IDS (Kali Linux)
        ↓
Alert Log Generation
        ↓
Splunk Indexing (botsv2)
        ↓
SPL Query Execution
        ↓
SOC Monitoring Dashboard

📊 Key Monitoring Dashboards

The dashboard includes:
Total Alerts Count
Critical / High / Medium / Low Alerts
Alert Trend (Time-based analysis)
Top Attacker IP
Top Targeted Server
Scanning Activity Detection
External vs Internal Traffic Analysis
Alerts by Signature
Alerts by Country

🔎 Sample SPL Queries
🔹 Detect Repeated Attacks from Same Source
index=botsv2 sourcetype=suricata event_type=alert
| stats count by src_ip
| where count > 5
| sort - count

🔹 Severity-Based Alert Filtering
index=botsv2 sourcetype=suricata alert.severity<=2

🔹 External Traffic Detection
index=botsv2 sourcetype=suricata event_type=alert
| eval traffic_type=if(cidrmatch("10.0.0.0/8", src_ip), "Internal", "External")
| stats count by traffic_type

🧠 IDS Fields Analyzed

Timestamp
Source IP
Destination IP
Protocol
Destination Port
Signature / Rule Name
Severity
Action (Allowed / Blocked)

🚨 Attack Patterns Observed

Port scanning behavior
Repeated alerts from same IP
Unusual traffic on sensitive ports
Medium severity intrusion attempts
Reconnaissance activity

🛡️ SOC Analyst Workflow Simulation

✔ Alert validation
✔ Severity classification
✔ Scanning detection
✔ IP reputation review
✔ Recommendation for blocking malicious IPs
✔ Escalation to L2 (if required)

⚠️ Limitation & Mitigation

Splunk Enterprise Security data model was not available in this lab environment.
To overcome this, all analysis was performed directly on raw Suricata logs using custom SPL queries.

This demonstrates strong foundational SOC skills without relying on prebuilt data models.

🎓 Skills Demonstrated

IDS Log Analysis
SIEM Monitoring
SPL Query Writing
Alert Triage
Threat Detection
Dashboard Creation
SOC L1 Workflow Understanding

📂 Repository Structure
📁 SOC-IDS-Project
 ├── README.md
 ├── Project Documentation (PDF/DOCX)
 ├── Dashboard Screenshots
 └── SPL Queries

👨‍💻 Author

Swarupananda Das
Aspiring SOC Analyst | Cybersecurity Enthusiast

🔗 LinkedIn: (Add Your LinkedIn Link Here)
🔗 GitHub: (Add Your GitHub Link Here)

📌 Conclusion

This project reflects hands-on experience in real-world IDS monitoring and threat detection using Splunk in a simulated SOC environment. It demonstrates readiness for entry-level SOC Analyst roles by showcasing practical log analysis, alert triage, and investigation capabilities.
