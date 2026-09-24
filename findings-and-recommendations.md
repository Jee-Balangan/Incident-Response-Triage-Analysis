# Findings and Recommendations

## Key Findings

### 1. Exposed AWS Credentials Were Used for Unauthorized Activity
The investigation identified leaked AWS credentials that were used for cloud activity, including IAM-related actions and EC2 activity.

This showed that exposed access keys can quickly lead to broader cloud compromise if they are not revoked immediately.

### 2. IAM Activity Indicated Account Misuse
Repeated IAM errors and access-key activity were observed early in the incident.

The volume and nature of the API activity suggested that the account was being used outside of normal administrative behavior.

### 3. Public S3 Access Created Additional Risk
An S3 bucket was made publicly accessible and files were uploaded.

This created unnecessary exposure and demonstrated the need for stronger cloud configuration controls and routine permission reviews.

### 4. Persistence Was Established Across Windows and Linux Systems
New user accounts were created on both Windows and Linux systems.

This provided the attacker with additional access paths and demonstrated the importance of monitoring unauthorized account creation.

### 5. PowerShell Was Used for Malicious Activity
PowerShell activity included outbound communication, file retrieval, and Base64-related behavior.

This showed the need for stronger PowerShell logging and detection rules focused on suspicious command-line behavior.

### 6. Command-and-Control Communication Was Observed
Compromised systems communicated with external infrastructure associated with attacker activity.

Outbound monitoring and correlation between endpoint and network telemetry were important for identifying this behavior.

### 7. Cryptomining Activity Was Confirmed
Network, DNS, endpoint protection, and performance telemetry showed evidence of cryptocurrency mining activity.

The combination of mining-domain traffic and abnormal CPU usage provided stronger evidence than either signal alone.

### 8. Email Was Used for Initial Access and Data Collection
The incident included malicious email attachments and creation of an Exchange transport rule that forwarded email to an external address.

This demonstrated both phishing risk and the importance of monitoring suspicious mailbox and transport-rule changes.

### 9. Customer Data Was Exposed
The investigation confirmed exposure of customer email addresses.

This increased the impact of the incident beyond unauthorized system access and required a higher level of response.

## Recommended Actions

### Immediate Containment

- Isolate compromised endpoints.
- Preserve forensic images where appropriate.
- Revoke exposed AWS access keys.
- Reset credentials for affected accounts.
- Block known command-and-control infrastructure.
- Review unauthorized account creation and confirm that no additional accounts were created or misused.
- Revoke public access to affected S3 resources.

### Cloud Security Improvements

- Enforce MFA for IAM users.
- Review IAM permissions for excessive access.
- Rotate exposed or potentially compromised credentials.
- Audit S3 permissions regularly.
- Apply least-privilege access controls to cloud resources.

### Endpoint and PowerShell Controls

- Improve PowerShell logging and monitoring.
- Alert on suspicious Base64-related PowerShell activity.
- Consider PowerShell Constrained Language Mode where appropriate.
- Apply security updates to affected Windows and Linux systems.
- Monitor unauthorized local account creation.

### Detection Improvements

- Correlate failed authentication attempts with later successful logins.
- Monitor DNS activity for known cryptomining destinations.
- Correlate mining-domain activity with abnormal CPU utilization.
- Monitor for suspicious email forwarding and transport-rule changes.
- Detect unauthorized S3 permission changes.
- Improve correlation across cloud, endpoint, DNS, email, and network telemetry.

### SOC Process Improvements

Update incident-response and SOC playbooks to include:

- Exposed AWS credentials
- Unauthorized IAM activity
- Public S3 access
- Suspicious PowerShell activity
- Cryptomining
- Unauthorized account creation
- Malicious email attachments
- Suspicious email forwarding rules
- Cross-platform incident correlation

## Key Lesson

The investigation showed that individual alerts may appear unrelated when viewed separately.

Correlating cloud, endpoint, network, DNS, and email activity made it possible to identify the incident as a broader multi-stage compromise and prioritize containment more effectively.
