# Investigation Timeline

This timeline reconstructs the major events identified during the incident investigation.

## Timeline of Key Events

### 09:08 UTC — IAM Errors Begin
Repeated AWS IAM errors were observed, including failed attempts to create access keys.

### 09:16 UTC — Access Key Activity
An attempt was made to create a new IAM access key for a user account.

AWS and GitGuardian notifications were also generated for leaked credentials.

### 09:16 UTC — EC2 Activity
An EC2 instance was launched using an Ubuntu AMI.

### 09:27 UTC — AWS API Activity
AWS account information was queried using the exposed credentials.

### 09:36–11:24 UTC — Linux Reconnaissance and Persistence
Root-level activity included password-file reconnaissance and creation of a new Linux user account.

### 09:43–09:55 UTC — Malicious Email Activity
A malicious email attachment was delivered and decoded into a macro-enabled spreadsheet.

### 09:55 UTC — Malicious Process Execution
Sysmon telemetry confirmed execution of a suspicious executable launched from the malicious document.

### 09:57 UTC — OneDrive Activity
A suspicious shortcut file was uploaded through OneDrive.

### 10:08 UTC — Windows Persistence
A new Windows account was created and added to the local Administrators group.

### 10:42 UTC — Malicious Executable Written
A suspicious executable was written to a Windows endpoint.

### 10:47–10:48 UTC — Command-and-Control Activity
PowerShell established outbound communication with external infrastructure and downloaded a file.

### 11:08–11:13 UTC — Base64 Activity
PowerShell activity decoded Base64 content and resulted in files being written to the `/tmp` directory.

### 11:21 UTC — Email Collection
A new Exchange transport rule was created to blind-copy email to an external address.

### 11:43–11:44 UTC — Expired Account Access
An expired account successfully authenticated from an external IP address.

### 13:01–13:57 UTC — S3 Exposure
An S3 bucket was made publicly accessible and files were uploaded.

### 13:17–13:52 UTC — Cryptomining Activity
Network telemetry confirmed mining-related traffic to known cryptomining infrastructure.

### 13:37 UTC — Endpoint Detection
Endpoint protection detected and blocked coin-mining activity on one affected host.

### 13:43–14:41 UTC — Web Defacement Activity
HTTP logs showed repeated access to an image associated with website defacement.

### 14:03–14:59 UTC — Mining-Related DNS Activity
DNS queries to cryptomining infrastructure were observed from an affected endpoint, alongside sustained high CPU usage.

### 14:47 UTC — Account Disabled
One compromised account was disabled.

### 15:15 UTC — Data Exposure Confirmed
An email referencing externally hosted content was reviewed and confirmed exposure of customer email addresses.

### 15:19 UTC — Additional Malicious Email Content
Another email containing an inline Base64-encoded image attachment was received.

## What the Timeline Showed

The incident was not limited to a single cloud alert. Activity expanded across cloud infrastructure, endpoints, user accounts, email, network traffic, and data exposure.

Correlating these events made it possible to identify a larger multi-stage compromise rather than treating each alert independently.
