# Android APK Reverse Engineering & Threat Triage

**Case type:** Mobile Threat Intelligence · Android Application Reverse Engineering  
**Assessment date:** 10 June 2026  
**Status:** Closed — partial analysis; final validation blocked  
**Sample:** `RTO-E-CHALAN.apk` · 8.2 MB  
**Reported domain:** `gffad.in`  
**Analysis tools:** Ghidra · APK reverse-engineering and signature-inspection tools  
**Author:** Parag Malvi

> **Scope note:** This case study documents the analysis activities and evidence currently available. The domain is recorded as investigator-reported; the repository does not yet include the original decompilation excerpt, hash output, certificate details, or network capture needed to independently validate every indicator.

## Executive Summary

On 10 June 2026, a suspicious Android application named `RTO-E-CHALAN.apk` (8.2 MB) was examined after being shared through WhatsApp with a challan-themed message. The sender was understood to be a previously compromised trusted contact, making the delivery context consistent with **trusted-account abuse and social engineering**.

The investigation focused on APK integrity and signature-related checks, reverse engineering, and identifying the application's external URL references. Ghidra was used during the analysis workflow, and `gffad.in` was reported as a domain associated with the application. Further validation was blocked by a password-protected component and laptop configuration limitations. The investigation was closed after partial analysis; the domain's role and the application's malicious behavior were not conclusively established.

## 1. Incident Context

The WhatsApp message used a challan-related pretext and urged the recipient to read the details in an attached APK. The sender was believed to be a trusted contact whose account had already been compromised.

This delivery pattern is consistent with:
- **Social engineering / pretexting:** using an official-sounding challan claim to prompt action.
- **Trusted-account abuse:** leveraging a familiar sender identity to increase the likelihood that a recipient will trust an attachment.
- **Malicious APK delivery:** distributing an Android package as the lure rather than a conventional document.

These describe the observed delivery context and plausible attack techniques; they do not, by themselves, prove the APK executed or performed credential theft.

## 2. Technical Investigation

### APK Integrity and Signature Inspection
Hash and signature-related checks were reportedly performed during the investigation. The original SHA-256 value, signing-certificate fingerprint, and verification output are not included in the current repository and should be added from the original analysis records.

### APK Reverse Engineering
APK decompilation and reverse-engineering work was reportedly carried out to inspect application contents and identify relevant indicators. A password prompt associated with a protected component interrupted further analysis. The exact protection mechanism and file type were not confirmed.

### Ghidra-Assisted Analysis
Ghidra was used as part of the reverse-engineering workflow. The available notes do not establish whether the analysed component was native code, a library, or another binary artefact. Any Ghidra screenshots or exported findings should identify the exact file analysed.

### URL / Indicator Investigation
The domain `gffad.in` was reported during the investigation as a URL associated with the application. It is documented here as an **investigator-reported indicator**, not as a verified malicious domain or confirmed command-and-control (C2) endpoint.

To validate this indicator, preserve the decompiled-code or resource excerpt showing the domain and its usage. Network evidence, if safely captured and attributable to the sample, could help determine whether the application actually connected to the domain and for what purpose.

## 3. Attack Technique Assessment

| Technique / concept | Relevance to this case | Confidence |
|---|---|---|
| Social engineering / pretexting | The message used a challan-related claim to encourage opening the attachment. | High for message context |
| Trusted-account abuse | The sender was reported to be a trusted contact whose account had already been compromised. | Investigator-reported |
| Malicious file delivery | An Android APK was delivered as the message attachment. | High for delivery; maliciousness unconfirmed |
| APK reverse engineering | Decompilation and inspection were used to investigate application contents. | Investigator-reported |
| Static indicator discovery | The investigation reportedly identified `gffad.in` as a domain associated with the app. | Needs original artefact verification |
| Credential theft / phishing payload | A possible risk to investigate given the lure, but no credential-harvesting behavior was confirmed. | Hypothesis only |
| Command-and-control (C2) communication | Cannot be concluded from a domain reference alone; runtime/network evidence is absent. | Unconfirmed |

**MITRE ATT&CK mapping (tentative):** *Phishing: Spearphishing via Service* (T1566.003) may be relevant to the use of a messaging service for delivery. This mapping is provisional and should not be treated as a confirmed technique attribution without stronger evidence about the delivery and execution chain.

## 4. Indicators of Compromise (IOC) Register

| Indicator | Value | Evidence status |
|---|---|---|
| APK filename | `RTO-E-CHALAN.apk` | Visible in the supplied screenshot |
| Sample size | 8.2 MB | Visible in the supplied screenshot |
| Domain | `gffad.in` | Investigator-reported; original code/network evidence pending |
| SHA-256 | Not included | Add exact output from original analysis |
| Signing-certificate fingerprint | Not included | Add exact verification output from original analysis |

Do not classify `gffad.in` as malicious solely because it was associated with the APK. Confirm its role through code context, reputation research, or attributable network evidence before publishing a definitive verdict.

## 5. Constraints and Closure Rationale

The investigation reached a partial reverse-engineering stage. A password prompt associated with a protected component and laptop configuration limitations prevented completion of further validation. The exact cause of the password prompt was not established.

The project was closed with the following outcomes:
- APK hash/signature-related checks and decompilation work were reported as performed.
- Ghidra was used during the analysis workflow.
- `gffad.in` was reported as an application-associated domain.
- The domain's purpose, any runtime connection, and the application's overall maliciousness remain unverified.

## 6. Conclusion

This case documents a challan-themed Android APK investigation involving suspected social engineering and trusted-account abuse. The work included reported APK integrity/signature checks, reverse engineering, Ghidra-assisted inspection, and URL investigation. Further analysis was blocked by a password-protected component and laptop configuration limitations.

**Final disposition:** Closed — partial reverse engineering completed; final validation inconclusive. The available evidence supports documenting a suspicious APK delivery and an investigator-reported domain, but does not establish credential theft, confirmed C2 traffic, or definitive malware classification.

## Evidence Image

The repository may include an anonymized copy of the WhatsApp screenshot at `evidence/whatsapp_apk_message.jpg`. Sender identity and personal information should remain redacted.

## Suggested GitHub Repository Metadata

**Repository name:** `android-apk-malware-triage`

**Description:** `Android APK threat triage and reverse engineering for a challan-themed WhatsApp lure, covering signature/hash inspection, Ghidra-assisted analysis, social-engineering assessment, and an investigator-reported URL indicator.`

**Topics:** `android-security` `malware-analysis` `apk-reverse-engineering` `ghidra` `threat-intelligence` `mobile-security` `social-engineering` `static-analysis`
