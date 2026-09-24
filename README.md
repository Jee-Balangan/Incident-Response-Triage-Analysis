# Incident-Response-Triage-Analysis
Incident response investigation focused on cloud activity, IAM misuse, endpoint telemetry persistence, and containment.

## Project Overview

In this project, I investigated a high-severity security incident using AWS CloudTrail data and SIEM telemetry. The investigation expanded from unusual IAM activity into a broader compromise involving cloud resources, Windows and Linux endpoints, persistence, cryptomining, malicious PowerShell activity, and data exposure.

My goal was to reconstruct the incident timeline, identify affected systems and accounts, map attacker behavior to MITRE ATT&CK, and recommend containment, prevention, and detection improvements.

## Investigation Scope

The incident involved activity across multiple security domains, including:

- AWS IAM misuse
- Exposed cloud credentials
- Unauthorized EC2 activity
- Public S3 bucket access
- Malicious email attachments
- Windows and Linux persistence
- PowerShell execution
- Command-and-control communication
- Cryptomining
- Web defacement
- Email-based data exfiltration

## Key Findings

The investigation identified:

- Compromised AWS credentials used for unauthorized cloud activity
- Attempts to create new IAM access keys
- Unauthorized EC2 instance activity
- Public exposure of an S3 bucket
- Persistence through newly created Windows and Linux accounts
- Malicious PowerShell and Base64-related activity
- Command-and-control communication from compromised endpoints
- Cryptomining activity confirmed through endpoint, DNS, and network telemetry
- Malicious files and scripts placed on affected systems
- Confirmed exposure of customer email data

## Incident Response Workflow

I worked through the incident by:

1. Reviewing the original AWS CloudTrail alert
2. Building a timeline of related activity
3. Correlating cloud, endpoint, DNS, email, and network evidence
4. Identifying compromised accounts and affected hosts
5. Reviewing persistence and privilege-related activity
6. Identifying command-and-control and cryptomining behavior
7. Mapping observed activity to MITRE ATT&CK
8. Prioritizing containment and remediation actions
9. Recommending detection and SOC process improvements

## MITRE ATT&CK Mapping

Observed techniques included:

- **T1078 – Valid Accounts**
- **T1136 – Create Account**
- **T1059 – Command and Scripting Interpreter**
- **T1105 – Ingress Tool Transfer**
- **T1505.003 – Server Software Component: Web Shell**
- **T1496 – Resource Hijacking**
- **T1491 – Defacement**
- **T1114.003 – Email Collection via Transport Rule**

## Recommended Actions

Key response and hardening recommendations included:

- Isolate and preserve compromised endpoints
- Revoke exposed AWS credentials
- Reset affected user credentials
- Enforce MFA for IAM users
- Review IAM permissions and reduce excessive access
- Audit and remediate public S3 permissions
- Block known command-and-control infrastructure
- Improve PowerShell detection
- Monitor cryptomining-related DNS activity
- Correlate failed and successful authentication events
- Strengthen phishing and credential-handling awareness
- Update SOC playbooks for cloud misuse, cryptomining, and encoded payloads

## Skills Demonstrated

- Incident response triage
- AWS CloudTrail analysis
- SIEM investigation
- Timeline reconstruction
- Cross-platform log correlation
- IAM security analysis
- Endpoint investigation
- Threat intelligence analysis
- MITRE ATT&CK mapping
- Containment and remediation planning
- Detection engineering
- SOC playbook improvement

## Takeaway

This investigation showed how a single cloud alert can reveal a much broader compromise when evidence is correlated across cloud, endpoint, DNS, email, and network telemetry. It reinforced the importance of cross-platform visibility, credential protection, and detection rules that connect related activity rather than treating individual alerts in isolation.
