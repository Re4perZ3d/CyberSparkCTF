## Challenge Description

This challenge is part of a beginner-level Cyber Threat Intelligence (CTI) CTF. It focuses on analyzing a real-world APT campaign named **ArcaneDoor**, leveraging the MITRE ATT&CK framework, CVE databases, and threat actor profiling. Participants are expected to identify key TTPs (Tactics, Techniques, and Procedures), malicious software, and exploited vulnerabilities.

---

## Questions & Answers

### What is the name of the group of the threat actor attributed to the ArcaneDoor campaign?

**Answer:** UAT4356, STORM-1849

### When was the ArcaneDoor campaign first observed? (Month year)

**Answer:** July 2023

### What kind of devices were primarily targeted by ArcaneDoor? (2 words)

**Answer:** networking devices

### What is the MITRE technique ID for exploitation of public-facing applications used in this campaign? (T****)

**Answer:** T1190

### ArcaneDoor leveraged VPN servers under their control for C2. What is the relevant sub-technique ID for this tactic? (T****.***)

**Answer:** T1583.003

### What are the ID and name of one of the two malicious software used in the ArcaneDoor campaign?

**Answer:** S1186–Line Dancer, S1188–Line Runner

### What vulnerability (CVE) did the threat actors exploit to trigger the execution of Line Runner?

**Answer:** CVE-2024-20353

### Which defensive mechanism did ArcaneDoor actors modify to bypass logging?

**Answer:** Authentication, Authorization, and Accounting (AAA) function

---

## Skills Learned

- 🔍 **Threat Actor Attribution**: Learned how to trace and confirm threat actor identities using public threat reports and naming conventions (e.g., UAT/STORM).
- 🧠 **MITRE ATT&CK Navigation**: Gained fluency in identifying and interpreting techniques and sub-techniques like `T1190` and `T1583.003`.
- 🛡️ **Vulnerability Research**: Understood the process of mapping CVEs to threat campaigns using security advisories and databases.
- 🐾 **TTP Analysis**: Strengthened knowledge of Tactics, Techniques, and Procedures (TTPs) used by advanced actors in real-world scenarios.
- ⚙️ **Defensive Evasion Techniques**: Identified how AAA mechanisms can be tampered with to evade detection and logging.

---

## Flag
Spark{W3lc0me_To_Thre4t_Int3ll1gence}
