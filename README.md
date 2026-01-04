# Deloitte-Cybersecurity-Job-Simulation-Log-Analysis-Case-Study

This repository documents my completion of Deloitte’s Cybersecurity Job Simulation on the Forage platform.  
The simulation focused on analyzing web activity logs to determine whether a suspected data breach could have occurred and to identify suspicious user behavior.

The purpose of this repository is to preserve my analysis, reasoning process, and conclusions as a long-term learning artifact.


## Scenario Overview

A client (Daikibo Industrials) experienced:
- A leak of sensitive internal information
- A production disruption affecting manufacturing lines
- Suspicion that their internal manufacturing status dashboard was compromised

I was tasked with analyzing provided web request logs to:
1. Determine whether the dashboard could be accessed directly from the internet
2. Identify suspicious activity within the logs


## Data Analyzed

- **File:** `web_requests.log`
- **Fields observed:**
  - Source IP address
  - Timestamp
  - HTTP method (GET / POST)
  - Request path
  - Response status code

All analysis was performed by manually reviewing request patterns and request sequences.


## Key Observations

### 1. Network Access
- All IP addresses observed were in the private range (`192.168.x.x`)
- No public IP addresses were present

**Conclusion:**  
The dashboard was not directly accessible from the public internet. Any access required internal network or VPN connectivity.


### 2. Normal User Behavior Pattern
A typical user session followed this sequence:
1. `POST /login` (credential submission)
2. `GET /` (dashboard access)
3. Requests for static resources (styles, scripts, images)
4. Occasional API calls for machine status

Timing between requests was irregular, consistent with human interaction.


### 3. Suspicious Activity Identified
One internal IP and user ID showed abnormal behavior:
- Repeated API requests to factory status endpoints
- Requests occurring at fixed, regular intervals
- Multiple requests at identical timestamps
- Frequent `401 Unauthorized` responses during API access
- Pattern not observed in other users

**Interpretation:**  
This behavior strongly suggests automated or misconfigured access rather than normal dashboard usage.


## Quiz Questions & Answers

### Q1: Could an attacker access the dashboard directly from the internet?
**Answer:** No  
**Reasoning:** All observed IP addresses were private, indicating no direct internet exposure.


### Q2: Which user ID showed the most suspicious activity?
**Answer:** `mdB7yD2dp1BFZPontHBQ1Z`  
**Reasoning:** This user ID was associated with automated request patterns and repeated unauthorized API access.


## Key Skills Demonstrated

- Log analysis and pattern recognition
- Understanding of HTTP methods (GET vs POST)
- Authentication and authorization behavior analysis
- Identifying automated vs human activity
- Evidence-based incident assessment
- Cybersecurity consulting-style reasoning


## Outcome

- Successfully completed Deloitte Cybersecurity Job Simulation
- Correctly answered all assessment questions
- Gained hands-on experience in internal incident investigation

