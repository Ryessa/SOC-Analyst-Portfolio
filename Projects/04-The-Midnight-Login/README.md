<h1>The Midnight Login</h1>
Status: In Progress<br>
<br>
A SOC investigation designed to develop practical skills in reviewing security events, analyzing evidence, establishing a timeline, and determining what occurred during suspicious activity.<br>
<br>
Focus: Alert Investigation • Log Analysis • Timeline Analysis • Incident Investigation • Security Documentation



<!--
<h3>Objective</h3>
# **The Midnight Login**

**SOC Analyst Investigation Template**

# **Status**

🟡 In Progress

# **Executive Summary**

On Saturday at, an authentication event involving Windows workstation was identified at approximately 2:40 AM. The activity occurred outside the user’s expected login period.

The login originated from \[SOURCE IP / LOCATION / SRV-FIN-02 , if known\] and targeted \[SYSTEM / APPLICATION / SRV-FIN-02 \].

The activity was selected for investigation because **\[briefly explain what made the login unusual — time, location, source IP, device, repeated failures, etc.\].**

The investigation focused on determining whether the authentication represented legitimate user activity, an authentication anomaly, or potential unauthorized account access.

**Initial Assessment:** Potentially Malicious

# **Scenario**

A security event was identified involving the account:

**Account:** s.aldosari 

**Authentication Time:** 02:31:31 

**Source IP**:10.20.4.15 

**Destination:** SRV-FIN-02,  / FINANCE FILE SERVER

**Authentication Result:** SUCCESS

The authentication required further investigation because:

* Authentication occurred outside expected hours.  
* The source IP had not previously been associated with the account.  
* Multiple authentication failures preceded the successful login.  
* The session came from another machine, not from someone sitting at the console.  
* Activity following authentication appeared inconsistent with expected user behavior.

# **Investigation Objective**

The objective of this investigation is to determine:

* Whether the authentication was legitimate.  
* Whether similar authentication activity occurred before or after the event.  
* Whether failed login attempts preceded the authentication.  
* Whether the source IP had previously interacted with the account or system.  
* Whether additional suspicious activity occurred after authentication.  
* Whether the available evidence indicates potential account compromise.

# **Lab Environment**

This investigation was conducted within a controlled cybersecurity lab environment.

## **Systems**

**Monitored Endpoint:** Workstation

**Hostname:** WS-042 

**Analyst System:** Windows

**SIEM:** \[Wazuh / Splunk / Other\]

**Virtualization Platform:** None

**Network Configuration:** \[Host-Only / NAT / Internal Network / Other\]

# **Tools Used**

## **ACTIVE DIRECTORY**

**Purpose:** Used to review alerts and authentication events associated with the account.

## **SECURITY.LOG**

**Purpose:** Used to examine authentication records and supporting system activity.

## **CMDB**

**Purpose:** Used to investigate network activity associated with the authentication event, if applicable.

## **MITRE ATT\&CK**

**Purpose:** Used to research and categorize observed behavior when sufficient evidence supported a technique mapping.

# **Initial Alert**

The investigation began after \[SIEM / LOG SOURCE / ALERT\] identified an authentication event involving:

| Field | Value |
| :---- | :---- |
| Timestamp | \[DATE/TIME\] |
| Username | \[USERNAME\] |
| Source IP | \[IP ADDRESS\] |
| Destination | \[HOST/SYSTEM\] |
| Event ID | \[EVENT ID, if applicable\] |
| Authentication Result | \[SUCCESS/FAILURE\] |
| Alert Severity | \[LEVEL, if applicable\] |

## **Why the Alert Required Investigation**

\[Explain why this event was significant.\]

At this stage, the event was treated as \[an anomaly / suspicious authentication / event requiring validation\] rather than confirmed malicious activity.

# **Evidence Collected**

The following evidence was reviewed during the investigation:

* ☐ SIEM alerts  
* ☐ Successful login events  
* ☐ Failed login events  
* ☐ Source IP addresses  
* ☐ Destination systems  
* ☐ User/account activity  
* ☐ Network traffic  
* ☐ Endpoint events  
* ☐ Other: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Relevant screenshots and artifacts were preserved throughout the investigation.

# **Investigation**

## **Step 1 — Validate the Initial Authentication Event**

The initial authentication event was reviewed to establish the basic facts of the incident.

**Observed**

Timestamp: \[TIME\]

Account: \[USERNAME\]

Source: \[SOURCE IP/HOST\]

Destination: \[DESTINATION\]

Result: \[SUCCESS/FAILURE\]

**Analysis**

\[Explain what this information tells you.\]

**Significance**

\[Explain why the event is or is not significant.\]

## **Step 2 — Establish the Account's Authentication History**

Authentication events involving \[USERNAME\] were reviewed for the period:

Start: \[TIME\]

End: \[TIME\]

The purpose was to determine whether the midnight login was an isolated event or part of a larger sequence.

**Findings**

\[Document what you actually found.\]

## **Step 3 — Investigate Failed Authentication Attempts**

Search for authentication failures preceding the successful login.

| Time | Account | Source IP | Destination | Result |
| :---- | :---- | :---- | :---- | :---- |
| \[TIME\] | \[USER\] | \[IP\] | \[HOST\] | Failed |
| \[TIME\] | \[USER\] | \[IP\] | \[HOST\] | Failed |
| \[TIME\] | \[USER\] | \[IP\] | \[HOST\] | Successful |

**Analysis:** \[Explain whether a meaningful pattern exists.\]

Do not assume that failed logins automatically indicate an attack. Consider alternative explanations such as mistyped passwords, expired credentials, automated services, or legitimate administrative activity.

## **Step 4 — Investigate the Source**

**Source IP:** \[IP ADDRESS\]

**Hostname:** \[IF KNOWN\]

**Network:** \[INTERNAL / EXTERNAL\]

**Previously Observed:** \[YES / NO / UNKNOWN\]

**Analysis:** \[Explain what you learned about the source.\]

Avoid writing that an IP address was malicious unless you have evidence supporting that conclusion. Instead, describe the observed activity associated with the source.

## **Step 5 — Compare Related Authentication Events**

Events involving the same username, source IP, destination, and authentication method were compared.

Correlation:

\[EVENT\]  
   ↓  
\[EVENT\]  
   ↓  
\[EVENT\]  
   ↓  
\[AUTHENTICATION\]

**Analyst Observation:** \[Explain why the relationship between these events matters.\]

## **Step 6 — Investigate Post-Login Activity**

Events occurring after the authentication were reviewed to determine what happened after access was obtained.

* Processes launched  
* Commands executed  
* PowerShell activity  
* Network connections  
* File access  
* Account changes  
* Privilege changes  
* Additional authentication  
* Security configuration changes

**Findings:** \[Document only what you actually observed.\]

**Analysis:** \[Explain whether the post-login behavior appears expected, unusual, or suspicious.\]

# **Event Timeline**

Build the timeline only from evidence you actually collected.

| Time | Event | Source | Significance |
| :---- | :---- | :---- | :---- |
| \[TIME\] | \[EVENT\] | \[LOG SOURCE\] | \[WHY IT MATTERS\] |
| \[TIME\] | \[EVENT\] | \[LOG SOURCE\] | \[WHY IT MATTERS\] |
| \[TIME\] | \[EVENT\] | \[LOG SOURCE\] | \[WHY IT MATTERS\] |
| \[TIME\] | \[EVENT\] | \[LOG SOURCE\] | \[WHY IT MATTERS\] |

# **Investigation Indicators**

Document relevant artifacts discovered during the investigation.

| Type | Indicator | Context |
| :---- | :---- | :---- |
| Username | \[USERNAME\] | \[CONTEXT\] |
| Source IP | \[IP ADDRESS\] | \[CONTEXT\] |
| Destination | \[HOST\] | \[CONTEXT\] |
| Event ID | \[EVENT ID\] | \[CONTEXT\] |
| Process | \[PROCESS\] | \[CONTEXT\] |

Not every artifact is necessarily an Indicator of Compromise. Only classify something as an IOC when the evidence supports doing so.

# **MITRE ATT\&CK Mapping**

Only add techniques supported by your investigation.

| Tactic | Technique | ID | Evidence |
| :---- | :---- | :---- | :---- |
| Privilege Escalation | Valid Accounts | T1078  | \[OBSERVED EVIDENCE\] |

**Mapping Explanation:** \[Explain why the observed behavior maps to the selected technique.\]

Do not add MITRE techniques simply to make the project appear more advanced.

# **Findings**

The investigation identified the following:

1. \[Finding \#1\]  
2. \[Finding \#2\]  
3. \[Finding \#3\]  
4. \[Finding \#4\]

**Key Correlation:** \[Explain the strongest correlation between your evidence.\]

# **Analyst Assessment**

**Classification:** \[Benign / Expected Activity / Suspicious / Potential Account Compromise / Confirmed Unauthorized Access / Inconclusive\]

**Confidence:** \[Low / Moderate / High\]

**Reasoning:** \[Explain why the evidence supports your classification.\]

**Observed fact:** \[What the logs/evidence directly show.\]

**Analyst assessment:** \[What you believe those facts indicate.\]

# **Analyst Conclusion**

Based on the available evidence, \[summarize what most likely occurred\].

The investigation established that \[summarize the strongest evidence\].

\[Explain whether the evidence was sufficient to classify the event as legitimate, suspicious, or malicious.\]

If this event occurred in a production environment, \[describe appropriate escalation, containment, validation, or additional investigation\].

Because this investigation was conducted in a controlled lab environment, the activity was generated for cybersecurity training and analysis.

# **Remediation Recommendations**

If comparable activity occurred in a production environment, recommended actions could include:

* Validate activity with the account owner.  
* Reset credentials if compromise is suspected.  
* Revoke suspicious sessions.  
* Review multifactor authentication.  
* Investigate the source IP.  
* Review endpoint activity.  
* Examine other accounts for similar behavior.  
* Escalate confirmed suspicious activity according to incident-response procedures.

Only include recommendations relevant to your actual findings.

# **Lessons Learned**

This investigation strengthened my understanding of \[SKILL\], \[SKILL\], and \[SKILL\].

The most important lesson from the investigation was: \[Explain what you learned.\]

I also gained practical experience with:

* \[Skill\]  
* \[Skill\]  
* \[Skill\]  
* \[Skill\]

If I repeated this investigation, I would: \[Explain what you would improve or investigate differently.\]

# **Screenshots and Evidence**

## **Figure 1 — Initial Alert**

**Insert:** \[SCREENSHOT\]

**Description:** \[Explain what the screenshot shows.\]

**Why It Matters:** \[Explain why this evidence is relevant to the investigation.\]

## **Figure 2 — Authentication Activity**

**Insert:** \[SCREENSHOT\] 

**Description:** \[Explain what the screenshot shows.\]

**Why It Matters:** \[Explain why this evidence is relevant to the investigation.\]

## **Figure 3 — Event Correlation**

**Insert:** \[SCREENSHOT\]

**Description:** \[Explain what the screenshot shows.\]

**Why It Matters:** \[Explain why this evidence is relevant to the investigation.\]

## **Figure 4 — Post-Authentication Activity**

**Insert:** \[SCREENSHOT\]

**Description:** \[Explain what the screenshot shows.\]

**Why It Matters:** \[Explain why this evidence is relevant to the investigation.\]

# **Final Assessment**

**Incident:** The Midnight Login

**Date:** \[DATE\]

**Account:** \[USERNAME\]

**Source:** \[SOURCE IP/HOST\]

**Destination:** \[TARGET\]

**Classification:** \[CLASSIFICATION\]

**Severity:** \[LOW / MEDIUM / HIGH / CRITICAL\]

**Confidence:** \[LOW / MODERATE / HIGH\]

**MITRE ATT\&CK:** \[TECHNIQUE — ID, if applicable\]

**Environment:** Controlled Cybersecurity Lab

**Investigation Status:** \[OPEN / CLOSED / ESCALATED\] -->
