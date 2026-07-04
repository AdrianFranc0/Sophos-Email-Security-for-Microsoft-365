# Sophos Email Security for Microsoft 365

## Executive Summary

This project demonstrates the deployment, validation, and operational use of **Sophos Email Security** within a Microsoft 365 enterprise environment.

A fictional organization, **FalsoTech**, was created to simulate how an IT/security administrator integrates Sophos Email Security with Microsoft 365, validates email protection, investigates processed messages, and manages sender allow/block controls.

Rather than simply demonstrating Sophos features, this project follows an enterprise email security administration workflow that mirrors how administrators deploy, validate, investigate, remediate, and continuously monitor email security controls.

Throughout this project, Sophos Email Security was used to protect Microsoft 365 mailboxes, inspect external email traffic, investigate suspicious messages, block an untrusted sender, allow a trusted sender, and maintain visibility through ongoing monitoring.

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| Sophos Central | Cloud security management platform |
| Sophos Email Security | Email protection and policy enforcement |
| Microsoft 365 | Enterprise email and productivity platform |
| Exchange Online | Cloud-based email service |
| Microsoft Entra ID | Identity and user synchronization |
| Microsoft Graph API | Secure Microsoft 365 integration |
| Outlook | Email testing and validation |

---

# Skills Demonstrated

- Sophos Central Administration
- Sophos Email Security
- Microsoft 365 Mailflow
- Exchange Online Administration
- Microsoft Entra ID Synchronization
- Microsoft Graph API Permissions
- Email Security Policy Review
- Message History Investigation
- Sender Allow/Block Management
- Spam Classification Review
- Email Threat Remediation
- Continuous Email Security Monitoring

---

# Lab Topology

<p align="center">
Sophos Email Security for Microsoft 365 Topology<br/>
<img src=https://i.imgur.com/3uHwtAl.png width="1000" style="height:auto;" alt="Sophos Email Security topology showing Microsoft 365, Exchange Online, Sophos Email Security, and FalsoTech users."/>
<br /><br />
</p>

---

# Microsoft Entra ID Synchronization

## Objective

The first phase of the deployment focused on integrating Sophos Email Security with Microsoft Entra ID to establish centralized user synchronization.

This integration allows Sophos to securely synchronize Microsoft 365 users and groups using Microsoft Graph API, ensuring protected mailboxes are automatically imported into Sophos Central for email security administration.

---

## Directory Synchronization

To establish communication between Sophos Email Security and Microsoft 365, a Microsoft Entra ID application was registered and granted the required Microsoft Graph API permissions.

After successful authentication, Sophos synchronized the FalsoTech Microsoft 365 directory, importing users and groups into the email security platform. This synchronization enables administrators to manage protected mailboxes without manually creating users inside Sophos Central.

<p align="center">
Microsoft Entra ID Synchronization<br/>
<img src=https://i.imgur.com/09Dd9jf.png width="950" style="height:auto;" alt="Sophos Email Security synchronized with Microsoft Entra ID using Microsoft Graph API."/>
<br /><br />
</p>

---

## Validation

Directory synchronization completed successfully, importing organizational users and groups into Sophos Email Security.

This established the foundation for the remainder of the project by ensuring protected Microsoft 365 mailboxes were available for policy assignment, mailflow integration, and email security administration.

# Microsoft 365 Mailflow Integration

## Objective

Following successful synchronization of Microsoft Entra ID users, the next phase focused on integrating Sophos Email Security with Microsoft 365 Mailflow.

This integration allows inbound and outbound email to be routed through Sophos Email Security for inspection before being returned to Microsoft 365 for final delivery.

---

## Mailflow Configuration

Sophos Email Security was configured using Microsoft 365 Mailflow, allowing the platform to inspect organizational email without requiring traditional MX record changes.

Unlike Secure Email Gateway deployments, Mailflow integration uses Microsoft 365 connectors to inspect email traffic while Exchange Online remains the organization's primary mail platform.

Post Delivery Protection was also enabled, allowing Sophos to perform additional analysis after delivery and initiate message clawback if an email is later determined to be malicious.

<p align="center">
Microsoft 365 Mailflow Integration<br/>
<img src=https://i.imgur.com/3DQdzXA.png width="950" style="height:auto;" alt="Sophos Email Security successfully integrated with Microsoft 365 Mailflow."/>
<br /><br />
</p>

---

## Validation

Mailflow integration was successfully established between Microsoft 365 and Sophos Email Security.

Following deployment, Sophos confirmed that email traffic was being processed through the configured mailflow connection, establishing the inspection path used throughout the remaining validation scenarios.

---

# Email Security Base Policy

## Objective

After Microsoft 365 Mailflow was configured, the next phase focused on reviewing the Sophos Email Security Base Policy.

The purpose of this section was to understand the layered security controls Sophos applies when processing inbound and outbound email.

---

## Base Policy Overview

The Sophos Email Security Base Policy provides the foundation for email inspection and policy enforcement within the environment.

This policy includes multiple protection layers such as sender authentication, anti-malware scanning, anti-spam detection, impersonation protection, URL analysis, and message handling actions.

These controls determine whether an email is delivered, blocked, quarantined, tagged, or returned to Microsoft 365 for final delivery processing.

<p align="center">
Sophos Email Security Base Policy Overview<br/>
<img src=https://i.imgur.com/O3YgiRQ.png width="950" style="height:auto;" alt="Sophos Email Security Base Policy overview showing layered email protection controls."/>
<br /><br />
</p>

---

## Policy Validation Purpose

Reviewing the Base Policy established an understanding of how Sophos evaluates email before the scenario-based validation began.

This provided the foundation for interpreting later results in Message History, including spam classification, sender blocking, allow-listing, and final message disposition.

---

# Email Processing Validation

## Objective

Following the deployment of Microsoft Entra ID synchronization, Microsoft 365 Mailflow integration, and the Sophos Email Security Base Policy, external test emails were generated to validate end-to-end email processing.

The objective was to establish baseline email activity before performing message investigations and administrative actions.

---

## Email Flow Validation

Several test emails were sent from an external email account to the FalsoTech users to verify that messages were successfully routed through Sophos Email Security.

These messages established the initial email traffic used throughout the remainder of the project and confirmed that Sophos was actively processing inbound email before administrative actions such as investigations, sender blocking, and allow-list validation were performed.

<p align="center">
External Email Processing Validation<br/>
<img src=https://i.imgur.com/7WGLwXJ.png width="950" style="height:auto;" alt="External email messages successfully processed through Sophos Email Security before administrative validation."/>
<br /><br />
</p>

---

## Validation

The successful delivery of multiple external messages confirmed that Microsoft 365 Mailflow and Sophos Email Security were operating as expected.

With baseline email traffic established, the environment was ready for investigation, policy validation, and administrative response scenarios.

---

# Scenario 1 – Email Investigation

## Objective

After validating email processing, the first administrative scenario focused on investigating an external email using Sophos Email Security Message History.

The objective was to review how Sophos processed the message, determine its classification, and analyze the actions taken before the message was returned to Microsoft 365 for final delivery.

---

## Message Investigation

An external email was selected from Message History to simulate the investigation of a user-reported message.

Using Sophos Email Security, the message details were reviewed to examine the sender, recipient, subject, source IP address, message classification, and final processing result. This information provides administrators with the context needed to determine whether an email is legitimate or requires further administrative action.

<p align="center">
Scenario 1 – Email Investigation<br/>
<img src=https://i.imgur.com/uaG4FNw.png width="950" style="height:auto;" alt="Sophos Email Security Message History showing the investigation of an external email."/>
<br /><br />
</p>

---

## Findings

The investigation confirmed that Sophos successfully processed the external message through the configured Microsoft 365 Mailflow integration.

Message Details provided centralized visibility into the email, including the sender, recipient, subject, source IP address, processing category, and final delivery status. This information enables administrators to quickly evaluate suspicious emails and determine the appropriate response.

Sophos also provides the ability to **Initiate Clawback**, allowing administrators to retract a previously delivered email from user mailboxes if it is later determined to be malicious. This capability helps organizations rapidly contain phishing attacks and other email-based threats after delivery.

---

# Scenario 2 – Block Malicious Sender

## Objective

Following the investigation of the reported email, the next administrative action focused on preventing future messages from the untrusted sender.

The objective was to configure Sophos Email Security to block the sender and validate that subsequent messages were automatically rejected before reaching organizational mailboxes.

---

## Sender Block Configuration

The sender was added to the Sophos Email Security **Inbound Blocked Senders** list through the Allow and Block settings.

Blocking a sender provides administrators with a straightforward method of preventing future email communication from known malicious or untrusted sources without modifying broader email security policies.

<p align="center">
Scenario 2 – Block Malicious Sender Configuration<br/>
<img src=https://i.imgur.com/X0Kw0p2.png width="950" style="height:auto;" alt="Sophos Email Security configuration showing a blocked sender added to the inbound block list."/>
<br /><br />
</p>

---

## Block Validation

After the sender was added to the blocked senders list, another email was sent from the same external address to validate the configured control.

Sophos successfully identified the blocked sender during message processing and prevented the email from reaching the intended recipient. Message History confirmed that the policy was enforced and recorded the action taken against the message.

<p align="center">
Scenario 2 – Block Validation<br/>
<img src=https://i.imgur.com/tDeIv4J.png width="950" style="height:auto;" alt="Sophos Email Security Message History validating that the blocked sender policy successfully prevented email delivery."/>
<br /><br />
</p>

---

## Findings

The validation confirmed that Sophos Email Security successfully enforced the blocked sender policy.

By adding the sender to the inbound block list, subsequent messages from the same address were automatically identified and prevented from being delivered. This administrative control provides organizations with an effective method of mitigating repeated phishing attempts or other unwanted email communications from known malicious senders.

---

# Scenario 3 – Allow Trusted Sender

## Objective

Following validation of the blocked sender policy, the final administrative scenario focused on restoring communication from a trusted sender.

The objective was to demonstrate how Sophos Email Security administrators can resolve false positives by allowing legitimate senders while maintaining the organization's overall email security posture.

---

## Allow Sender Validation

The sender was added to the Sophos Email Security **Inbound Allowed Senders** list through the Allow and Block settings.

After updating the allow list, another email was sent from the same external address to validate the configuration. Sophos successfully processed the message and returned it to Microsoft 365 for final delivery.

The combined configuration and validation demonstrate how administrators can quickly restore communication with trusted senders while maintaining visibility into message processing through Sophos Email Security.

<p align="center">
Scenario 3 – Allow Trusted Sender Validation<br/>
<img src=https://i.imgur.com/m9HWtMv.png width="950" style="height:auto;" alt="Sophos Email Security allowing a trusted sender and validating successful email processing."/>
<br /><br />
</p>

---

## Findings

The validation confirmed that Sophos Email Security successfully processed email from the trusted sender after the allow list was updated.

Maintaining allow lists enables administrators to quickly resolve false positives while ensuring legitimate business communication continues without unnecessary interruption.

---

# Continuous Monitoring

## Objective

Following deployment, validation, and administrative testing, the final phase of the project focused on the importance of continuous monitoring within Sophos Email Security.

While security policies help prevent malicious email from reaching users, maintaining an effective email security posture requires ongoing visibility into email activity, policy enforcement, and emerging threats.

---

## Monitoring & Visibility

Sophos Email Security provides administrators with centralized visibility into processed email through monitoring and investigative tools that support day-to-day security operations.

### Message History

Message History provides administrators with detailed visibility into processed email, including sender information, recipients, message classification, delivery actions, and policy results.

This information assists with investigating suspicious messages, validating policy enforcement, and determining the appropriate administrative response.

---

### Allow and Block Management

Maintaining the Allow and Block lists is an important part of ongoing email administration.

As organizations receive new threats or identify legitimate senders that require exceptions, administrators can update these lists to maintain an effective balance between strong security and uninterrupted business communication.

---

### Policy Review

Email security policies should be reviewed periodically to ensure they continue aligning with organizational requirements and evolving email threats.

Regular policy reviews help administrators maintain effective protection while reducing unnecessary false positives and adapting to changes in organizational communication.

---

### Operational Visibility

Continuous monitoring enables administrators to verify that email security controls remain effective, identify suspicious activity, investigate reported messages, and respond to new threats as they emerge.

Rather than treating email security as a one-time deployment, ongoing monitoring helps organizations maintain a proactive security posture through continuous visibility and administrative oversight.

---

# Project Outcome

This project successfully demonstrated the deployment, integration, validation, and administration of Sophos Email Security within a Microsoft 365 enterprise environment.

Throughout the project:

- Microsoft Entra ID was integrated with Sophos Email Security to synchronize organizational users.
- Microsoft 365 Mailflow was configured to inspect inbound and outbound email.
- Sophos Email Security Base Policy protections were reviewed to understand the layered security controls applied during email processing.
- External email traffic was generated to validate end-to-end message processing.
- Message History was used to investigate processed email and evaluate security actions.
- Administrative controls were implemented to block an untrusted sender and restore communication with a trusted sender through the Allow and Block lists.
- Continuous monitoring practices were established to support ongoing visibility into email activity and policy effectiveness.

By combining deployment, investigation, remediation, and continuous monitoring, this project demonstrates practical hands-on experience administering Sophos Email Security within a Microsoft 365 environment while following workflows commonly performed by enterprise IT and cybersecurity administrators.
