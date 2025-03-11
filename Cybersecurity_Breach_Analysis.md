# 🔒 Equifax Data Breach (2017) - Analysis & Log Detection Tool

## 🎯 Objective
This project aims to analyze the **Equifax data breach (2017)** and provide a **Python-based log detection tool** to identify exploit attempts. The tool scans logs for suspicious activity related to unpatched vulnerabilities, such as the **Apache Struts CVE-2017-5638** exploited in the breach.

## Overview of the Breach
Equifax, one of the largest credit reporting agencies, suffered a massive data breach in 2017, exposing sensitive data of **147 million** people.  
- **Company Involved:** Equifax  
- **Date:** July 2017 (Discovered in September 2017)  
- **Attack Vector:** Apache Struts vulnerability (CVE-2017-5638)  
- **Type of Data Exposed:** Social Security numbers, birth dates, addresses  

## 📉 Impact Analysis
- **Financial Impact:** $700 million in settlements  
- **Reputational Damage:** Loss of public trust, CEO resignation  
- **Operational Consequences:** Security audits, lawsuits  

## 🔍 Lessons Learned
- **Vulnerability Exploited:** Unpatched Apache Struts framework  
- **Preventive Measures:** Timely patch management, threat monitoring  
- **Post-Breach Actions:** Equifax improved security protocols  

---  

## 🛠 Log Analysis Tool for Detecting Exploit Attempts
Below is a Python script that scans logs for **potential exploit attempts** on vulnerable endpoints, simulating how attacks like the Equifax breach can be detected.

```python
import re  

# Sample log data simulating an Apache Struts vulnerability attack  
log_data = """  
[2017-05-14 12:30:45] - User IP: 192.168.1.15 - Access: /vulnerable-endpoint - Exploit Attempt: True  
[2017-05-15 09:12:34] - User IP: 203.0.113.22 - Access: /admin - Exploit Attempt: False  
[2017-06-02 18:45:09] - User IP: 198.51.100.45 - Access: /vulnerable-endpoint - Exploit Attempt: True  
"""  

# Function to detect suspicious log entries  
def detect_breach(logs):  
    pattern = r"\[.*\] - User IP: (\d+\.\d+\.\d+\.\d+) - Access: (.*?) - Exploit Attempt: (True|False)"  
    matches = re.findall(pattern, logs)  

    print("🔍 Detected Exploit Attempts:")  
    for ip, endpoint, exploit in matches:  
        if exploit == "True":  
            print(f"⚠️  Suspicious activity detected! IP: {ip}, Endpoint: {endpoint}")  

# Run the function on sample logs  
detect_breach(log_data)
