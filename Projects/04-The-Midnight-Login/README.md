<h1>The Midnight Login</h1>
Status: In Progress<br>
<br>
A SOC investigation designed to develop practical skills in reviewing security events, analyzing evidence, establishing a timeline, and determining what occurred during suspicious activity.<br>
<br>
Focus: Alert Investigation • Log Analysis • Timeline Analysis • Incident Investigation • Security Documentation



<!--
# **The Midnight Login**

**SOC Analyst Investigation Template**

# **Status**

🟡 In Progress

# **Executive Summary**

On Saturday at, an authentication event involving Windows workstation was identified at approximately 2:40 AM. The activity occurred outside the user’s expected login period.

The login originated from 10.20.4.15 / WS-042 and targeted SRV-FIN-02.

The activity was selected for investigation because **of the repeated failures, the account pivoting, the times of the login occurred.**

The investigation focused on determining whether the authentication represented legitimate user activity, an authentication anomaly, or potential unauthorized account access.

**Initial Assessment:** suspicious authentication

# **Scenario**

At 02:40 on a Saturday at Nexa Digital. An alert fires on SRV-FIN-02, a finance file server. The rule that triggered is 'Multiple failed logons followed by success'. Nobody from the finance team is scheduled to work tonight. 

**Account:** M. Tariq

**Authentication Time:** 02:31:31 

**Source IP**:10.20.4.15 

**Destination:**  SRV-FIN-02 

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

**Log:** SIEM

**Virtualization Platform:** None

**Network Configuration:** Internal Network

# **Tools Used**

## **ACTIVE DIRECTORY**

**Purpose:** Provides centralized authentication and authorization to network resources. 

## **SECURITY.LOG**

**Purpose:** Used to examine authentication records and supporting system activity.

## **CMDB**

Used to investigate network activity associated with the authentication event, if applicable.

## **MITRE ATT\&CK**

Used to research and categorize observed behavior according to established adversary tactics and techniques.

# **Initial Alert**

The investigation began after Security.log identified an authentication event involving:

| Field | Value |
| :---- | :---- |
| Timestamp | 02:31:31 |
| Username | S. Aldosari |
| Source IP | 10.20.4.15  |
| Destination | SRV-FIN-02  |

## **Why the Alert Required Investigation**

This event was significant because of the unusual timestamp. The activity occurred outside of normal hours.

At this stage, the event was treated as suspicious authentication rather than confirmed malicious activity. Additional authentication events were examined.

# **Evidence Collected**

The following evidence was reviewed:

* Windows authentication events  
* Account name associated with events  
* Authentication timestamps  
* Source IP address  
* Failed and successful login activity  
* Hostname associated with assigned workstation

Relevant screenshots were preserved throughout the investigation.

# **Investigation**

## **Step 1 — Validate the Initial Authentication Event**

The initial authentication event was reviewed to establish the basic facts of the incident.

**Observed**

Timestamp: 02:31:31

Account: M. Tariq

Source: 10.20.4.15 

Destination: SRV-FIN-02 

Result: SUCCESS

**Analysis**

At 2:31:31 on Saturday morning, the SRV-FIN-02 finance file server was triggered by the ‘Multiple failed logons followed by success’ alert. This alert went off during outside normal hours and no one from the Finance team is scheduled to work that night. 

**Significance**

This significant event is evidence that someone was not seated at WS-042. 

## **Step 2 — Establish the Account's Authentication History**

Authentication events involving **M. Tariq** were reviewed for the period:

Start: 02:31:26

End: 02:31:31

There were no previous authentication events involving M. Tariq, however, there were several previous events involving other user accounts on the Finance team. Several failed authentication attempts were identified with hostnames S. Aldosari and A. Kamal. 

**Findings**

The credentials of S. Aldosari was used to log into WS-042. Several unsuccessful attempts were made on Aldosari's account to access SRV-FIN-02 . Afterwards, the credentials of A. Kamal was used in the same process but was unsuccessful. This led to the use of M. Tariq’s credentials to login and successfully access the system. 

The successful authentication originated from the same source IP address.

## **Step 3 — Investigate Failed Authentication Attempts**

![][image1]

Figure 1a.png

**Analysis:** 

The credentials of S. Aldosari were obtained and used to log into SRV-FIN-02 on the WS-042 workstation. This workstation is assigned to A. Kamal. After several failed attempts, A. Kamal’s credentials were used. A Logon type 3 was recorded with each event which indicates that the network session did not come from someone sitting at the console, but remotely.

This pattern is evident that existing account credentials were obtained and used to log into the workstation.

## **Step 4 — Investigate the Source**

**Source IP:** 10.20.4.15 

**Hostname:** WS-042 

**Network:** INTERNAL

**Previously Observed:** NO

**Analysis:** The source IP address **10.20.4.15** is associated with **WS-042**. This workstation is assigned to A. Kamal, an Analyst in the Finance Department. The normal business hours of that department are from 08:00 \- 17:00 (9:00 AM \- 5:00 PM).The event occurred outside of normal hours after 2:00 AM. There were five failed attempts under S. Aldosari’s account with the same source IP address of **10.20.4.15**.

## **Step 5 — Compare Related Authentication Events**

Events involving the same username, source IP, destination, and authentication method were compared.

Correlation:

S. Aldosari’s Account / 10.20.4.15  
   ↓  
A. Kamal’s Account / 10.20.4.15  
   ↓  
M. Tariq’s Account / 10.20.4.15  
   ↓  
\[AUTHENTICATION\]

**Analyst Observation:** The source IP address **10.20.4.15** was compared to related authentication events. The investigation found that the source IP address appeared repeatedly during both the failed and successful authentication activity. 

The relationship between these events matters because it displays pivoting, persistence, and escalation between several accounts.

## **Step 6 — Investigate Post-Authentication Activity**

Events occurring after the authentication were reviewed to determine what happened after access was obtained.

* Privilege changes

**Findings:** A post-authentication activity relieves that “special privileges assigned” for M. Tariq.

**Analysis:** \[Explain whether the post-login behavior appears expected, unusual, or suspicious.\]

# **Event Timeline**

![][image2]  
Figure 1.png

**Investigation Indicators**

Document relevant artifacts discovered during the investigation.

| Type | Indicator | Context |
| :---- | :---- | :---- |
| Username | S. Aldosari | Username Is not associated with Source IP |
| Source IP | 10.20.4.15 | Source associated with failed and successful logins |
| Destination | SRV-FIN-02  | Designation associated with successful login |

# **MITRE ATT\&CK Mapping**

The observed behavior was reviewed against the MITRE ATT\&CK framework.

**Mapping Explanation:** \[Explain why the observed behavior maps to the selected technique.\]

A potential mapping for the repeated login attempts is:

Tactic:Privilege Escalation  
Technique: Valid Accounts  
Technique ID: T1078 

# **Findings**

The investigation identified the following:

1. The attempts originated from the same source IP address **10.20.4.15**  
2. Multiple failed authentication attempts from several user accounts  
3. All events occurred outside of normal business hours  
4. An event occurred after successful authentication that requires review

**Key Correlation:** When several failed attempts are made using the existing credentials of one account, the unauthorized user pivots to another account to gain higher-level permissions.

**Observed fact:** Security.log

# **Analyst Conclusion**

Based on the available evidence, the authentication activity was assessed as Suspicious & Potential Account Compromise.

The strongest evidence was the correlation between repeated authentication failures and a successful login involving the same source IP address.

The evidence is sufficient to classify the event as suspicious because several existing account credentials were used: S. Aldosari, A. Kamal, and M. Tariq. Whenever one user account fails to obtain access to SRV-FIN-02, login credentials are used from another account\[Explain whether the evidence was sufficient to classify the event as legitimate, suspicious, or malicious.\]

If this event occurred in a production environment, the investigation must contain remediation by reviewing endpoint activity, review additional authentication sources,describe appropriate escalation, containment, validation, or additional investigation\].

Because this investigation was conducted in a controlled lab environment, the activity was generated for cybersecurity training and analysis.

# **Remediation Recommendations**

If comparable activity occurred in a production environment, recommended actions could include:

* Validate activity with the account owner.  
* Reset credentials  
* Revoke suspicious sessions.  
* Investigate the source IP address.  
* Review endpoint activity.  
* Examine other accounts for similar behavior.  
* Escalate confirmed suspicious activity according to incident-response procedures.

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

## **Figure 1 — Authentication Activity**

![][image3]

**Description:** Security.log of SRV-FIN-02 

**Why It Matters:** Provides authentication activity of SRV-FIN-02 prior to the security alert

## 

## **Figure 2 — Active Directory** 

![][image4]

**Description:** \[Explain what the screenshot shows.\]

**Why It Matters:** \[Explain why this evidence is relevant to the investigation.\]

## **Figure 3 — Dataset**

![][image5]

**Description:** \[Explain what the screenshot shows.\]

**Why It Matters:** \[Explain why this evidence is relevant to the investigation.\]

# **Final Assessment**

**Incident:** The Midnight Login

**Date:** Saturday, 02:31:31

**Affected Account(s):** S. Aldosar, A. Kamal, and M. Tariq

**Source:** 10.20.4.15 / WS-042 

**Destination:** SRV-FIN-02 

**Classification:** Suspicious Authentication Activity

**Severity:** HIGH

**MITRE ATT\&CK:** Valid Accounts / T1078 

**Environment:** Controlled Cybersecurity Lab \- LearnDefend

**Investigation Status:** CLOSED
