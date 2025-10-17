# 🔒 USB Password-Theft Awareness Toolkit (Educational / Defensive)

> ⚠️ **Legal & Ethical Notice**  
> This repository is for **educational, awareness, and defensive** purposes only. It **does not** contain working malware, exploit code, or step-by-step instructions to steal credentials.  
> Creating, distributing, or using tools to collect other people’s passwords without explicit written permission is **illegal and unethical**. Use this repository only for training, awareness presentations, or approved lab exercises in an isolated environment.

---

## Project Summary

This repo explains the concept of USB-based credential-theft attacks at a high level and provides practical **defensive** guidance: how the attack works conceptually, how to detect it, and how to harden systems and user behavior against it. All operationally actionable material that could enable misuse has been deliberately **omitted**.

> **Goal:** Raise awareness and provide clear, safe hardening/checklist material suitable for distribution to staff or inclusion in a security handbook.

---

## Table of Contents

- [What this describes (non-actionable)](#what-this-describes-non-actionable)  
- [Risks & Impact](#risks--impact)  
- [Safe Demonstration Guidance (for approved labs)](#safe-demonstration-guidance-for-approved-labs)  
- [Defensive Controls & Hardening (detailed)](#defensive-controls--hardening-detailed)  
- [Detection & Indicators of Compromise (IoCs)](#detection--indicators-of-compromise-iocs)  
- [Incident Response Checklist](#incident-response-checklist)  
- [User Awareness & Training Recommendations](#user-awareness--training-recommendations)  
- [Appendix: Demo Approval Template (optional)](#appendix-demo-approval-template-optional)  
- [Contact / Author](#contact--author)

---

## What this describes (non-actionable)

At a conceptual level, a USB-based credential-theft scenario typically involves:

- A physical removable device that is delivered to or plugged into a target machine.
- Some mechanism (scripted automation or manual execution) that attempts to extract locally stored credentials or system information.
- Reliance on human behavior (plugging unknown drives, launching unfamiliar files) and misconfigured systems.

> **Important:** This document **does not** provide the code or commands to perform such an attack. Any references to utilities or filenames in training materials are for identification only and are intentionally non-actionable.

---

## Risks & Impact

- **Direct account compromise:** Browser- or system-stored credentials can give immediate access to services.
- **Lateral movement:** Harvested credentials may be reused to access internal systems.
- **Persistence & escalation:** Stolen credentials can be leveraged to obtain long-term access or privileges.
- **Operational disruption & reputational loss.**

---

## Safe Demonstration Guidance (for approved labs)

If you must demonstrate concepts for training:

1. **Obtain written approval** from management and legal.
2. Use a **dedicated, isolated VM** with no network access to production resources.
3. Populate the VM with **dummy accounts and fake credentials only**.
4. Document the scope, goals, and cleanup steps in advance.
5. Never deploy any demo material outside the lab environment.

---

## Defensive Controls & Hardening (detailed)

### 1. Operating System & Policy
- Disable AutoPlay/AutoRun for removable media centrally via Group Policy (Windows) or equivalent MDM controls.
- Keep OS and endpoint software fully patched.
- Enforce **least privilege** (users run non-admin accounts by default).

### 2. Endpoint Protection
- Deploy EDR (Endpoint Detection & Response) and ensure it is configured to alert on processes launched from removable volumes.
- Implement application whitelisting (e.g., AppLocker, WDAC) to prevent unauthorized executables from running.
- Use device control / DLP (Data Loss Prevention) to block or audit copying of sensitive files to removable media.

### 3. USB & Peripheral Management
- Restrict use of removable storage: require company-issued, encrypted USBs when necessary.
- Configure read-only policies or disable USB mass-storage where possible.
- Maintain inventory and logging of USB devices connected to endpoints.

### 4. Credential Hygiene
- Discourage saving critical passwords in browsers; provide a company-approved password manager instead.
- Enforce Multi-Factor Authentication (MFA) for all sensitive systems.
- Regularly rotate and audit privileged credentials.

### 5. Physical & Operational Measures
- Do not leave workstations unattended; enable automatic locking after short inactivity.
- Train reception/office staff to handle found media as suspicious (do not plug into corporate machines).
- Provide secure alternatives for file transfer (managed file share, SFTP, enterprise cloud).

---

## Detection & Indicators of Compromise (IoCs)

Investigate when you see:

- Files with unexpected names or unknown executables on removable drives.
- Process creation events where the parent process is associated with a removable volume.
- Sudden creation of plaintext files containing lists of accounts or system configuration on removable media.
- EDR alerts for suspicious access to browser profile directories or credential stores.
- Unusual outbound connections following USB insertion.

---

## Incident Response Checklist (quick actions)

1. **Isolate** the suspect host from the network.  
2. **Preserve evidence** (do not reboot, document timestamps, collect relevant logs).  
3. **Collect logs**: EDR, Windows Event Logs, USB device history, and process creation traces.  
4. **Quarantine** the removable device securely for forensic analysis.  
5. **Reset credentials** that may have been compromised and require MFA re-registration.  
6. **Perform forensic analysis** to determine scope and lateral movement.  
7. **Report** to internal security and legal/compliance teams.

---

## User Awareness & Training Recommendations

- Short, frequent reminders: **“Don’t plug unknown USB drives”**.
- Run controlled USB-drop campaigns and remediate via targeted training.
- Teach how to view hidden files and how to check removable media safely.
- Provide accessible secure file-transfer options and enterprise password managers.

---

## Appendix: Demo Approval Template (optional)

> Use this template to request permission before conducting a lab/demonstration. Include: objective, scope, VMs used, network isolation method, data used (dummy only), participants, start/end time, and cleanup actions.

---

## Contact / Author

Security Awareness Team — Educational Materials  
For a customized defensive checklist, detection playbook, or slide deck summarizing this content, contact your internal security team or request a consultant.

---

## License

This repository is licensed for **educational and defensive** use only. Any malicious or unauthorized use of the concepts described here is strictly prohibited.

