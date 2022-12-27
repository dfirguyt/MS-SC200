https://learn.microsoft.com/en-us/training/modules/remediate-azure-defender-security-alerts/

# Introduction

Microsoft Defender for Cloud provides a purpose-driven user interface to manage and investigate security incidents and alerts across protected resources. The alert includes actions to take to remediate the threat and steps to prevent future attacks.

You're a Security Operations Analyst working at a company that has deployed cloud workload protection with Defender for Cloud. You're responsible for remediating security alerts generated by Defender for Cloud detections.

You receive an alert regarding a container; the alert provides information to manually remediate the issue and what you can do in the future to prevent further attacks. You work with the infrastructure team to resolve the issue. The infrastructure team recommends creating automated remediation tasks for future alerts regarding the same problem. You create a Logic App to perform the actions for future alerts.

Learn how to remediate security alerts in Defender for Cloud.

# Understand security alerts

In Microsoft Defender for Cloud, there are various alerts for many different resource types. Defender for Cloud generates alerts for resources deployed on Azure and for resources deployed on on-premises and hybrid cloud environments. Security alerts are triggered by advanced detections and are available only with Defender for Cloud.

## Respond to today's threats

There have been significant changes in the threat landscape over the last 20 years. In the past, companies typically only had to worry about website defacement by individual attackers who were mostly interested in seeing "what they could do". Today's attackers are much more sophisticated and organized. They often have specific financial and strategic goals. They also have more resources available to them, as they might be funded by nation states or organized crime.

These changing realities have led to an unprecedented level of professionalism in the attacker ranks. No longer are they interested in web defacement. They're now interested in stealing information, financial accounts, and private data – all of which they can use to generate cash on the open market or use a particular business, political, or military position. Even more concerning than those attackers with a financial objective are the ones who breach networks to harm infrastructure and people.

In response, organizations often deploy various point solutions focused on defending either the enterprise perimeter or endpoints by looking for known attack signatures. These solutions tend to generate a high volume of low fidelity alerts, which require a security analyst to triage and investigate. Most organizations lack the time and expertise required to respond to these alerts – so many go unaddressed.

In addition, attackers have evolved their methods to subvert many signature-based defenses and adapt to cloud environments. New approaches are required to more quickly identify emerging threats and expedite detection and response.

## What are security alerts and security incidents?

Alerts are the notifications that Defender for Cloud generates when it detects threats on your resources. Defender for Cloud prioritizes and lists the alerts, along with the information needed for you to quickly investigate the problem. Defender for Cloud also provides recommendations for how you can remediate an attack.

A security incident is a collection of related alerts instead of listing each alert individually. Defender for Cloud uses Cloud Smart Alert Correlation to correlate different alerts and low fidelity signals into security incidents.

With security incidents, Defender for Cloud provides you with a single view of an attack campaign and all of the related alerts. This view enables you to quickly understand what actions the attacker took, and what resources were affected. For more information, see Cloud smart alert correlation.

## How does Defender for Cloud detect threats?

Microsoft security researchers are constantly on the lookout for threats. Because of our global presence in the cloud and on-premises, we have access to an expansive set of telemetry. The wide-reaching and diverse collection of datasets enable us to discover new attack patterns and trends across our on-premises consumer and enterprise products, as well as our online services. As a result, Defender for Cloud can rapidly update its detection algorithms as attackers release new and increasingly sophisticated exploits. This approach helps you keep pace with a fast-moving threat environment.

To detect real threats and reduce false positives, Defender for Cloud collects, analyzes, and integrates log data from your Azure resources and the network. It also works with connected partner solutions, like firewall and endpoint protection solutions. Defender for Cloud analyzes this information, often correlating information from multiple sources, to identify threats.

Defender for Cloud employs advanced security analytics, which go far beyond signature-based approaches. Breakthroughs in big data and machine learning technologies are used to evaluate events across the entire cloud fabric – detecting threats that would be impossible to identify using manual approaches and predicting the evolution of attacks. These security analytics include:

-   **Integrated threat intelligence**: Microsoft has an immense amount of global threat intelligence. Telemetry flows in from multiple sources, such as Azure, Microsoft 365, Microsoft CRM online, Microsoft Dynamics AX, outlook.com, MSN.com, the Microsoft Digital Crimes Unit (DCU), and Microsoft Security Response Center (MSRC). Researchers also receive threat intelligence information shared among major cloud service providers and feeds from other third parties. Defender for Cloud can use this information to alert you to threats from known bad actors.
    
-   **Behavioral analytics**: Behavioral analytics is a technique that analyzes and compares data to a collection of known patterns. However, these patterns aren't simple signatures. They're determined through complex machine learning algorithms that are applied to massive datasets. They're also determined through careful analysis of malicious behaviors by expert analysts. Defender for Cloud can use behavioral analytics to identify compromised resources based on analysis of virtual machine logs, virtual network device logs, fabric logs, and other sources.
    
-   **Anomaly detection**: Defender for Cloud also uses anomaly detection to identify threats. In contrast to behavioral analytics (which depends on known patterns derived from large data sets), anomaly detection is more "personalized" and focuses on baselines specific to your deployments. Machine learning is applied to determine normal activity for your deployments. Then, rules are generated to define outlier conditions that could represent a security event.
    

## How are alerts classified?

Defender for Cloud assigns a severity to alerts to help you prioritize the order in which you respond to each alert, so when a resource is compromised, you can get to it right away. The severity is based on how confident Defender for Cloud is in the finding, or the analytic used to issue the alert, and the confidence level that there was malicious intent behind the activity that led to the alert.

-   High: There's a high probability that your resource is compromised. You should look into it right away. Defender for Cloud has high confidence in both the malicious intent and in the findings used to issue the alert. For example, an alert detects the execution of a known malicious tool such as Mimikatz, a common tool used for credential theft.
    
-   Medium: This severity indicates it is probably a suspicious activity that might indicate that a resource is compromised. Defender for Cloud's confidence in the analytic or finding is medium, and the confidence of malicious intent is medium to high. These would usually be machine learning or anomaly-based detections. For example, a sign-in attempt from an anomalous location.
    
-   Low: This severity indicates it might be a benign positive or a blocked attack.
    
    -   Defender for Cloud isn't confident enough that the intent is malicious, and the activity might be innocent. For example, log clear is an action that might happen when an attacker tries to hide their tracks, but in many cases it's a routine operation performed by admins.
        
    -   Defender for Cloud doesn't usually tell you when attacks were blocked unless it's an interesting case that we suggest you look into.
        
-   Informational: You'll only see informational alerts when you drill down into a security incident or if you use the REST API with a specific alert ID. An incident is typically made up of many alerts, some of which might appear on their own to be only informational, but in the context of the other alerts might be worthy of a closer look.
    

## Continuous monitoring and assessments

Defender for Cloud benefits from having security research and data science teams throughout Microsoft who continuously monitor for changes in the threat landscape. This includes the following initiatives:

-   **Threat intelligence monitoring**: Threat intelligence includes mechanisms, indicators, implications, and actionable advice about existing or emerging threats. This information is shared in the security community, and Microsoft continuously monitors threat intelligence feeds from internal and external sources.
    
-   **Signal sharing**: Insights from security teams across Microsoft's broad portfolio of cloud and on-premises services, servers, and client endpoint devices are shared and analyzed.
    
-   **Microsoft security specialists**: Ongoing engagement with teams across Microsoft that work in specialized security fields, like forensics and web attack detection.
    
-   **Detection tuning**: Algorithms are run against real customer data sets, and security researchers work with customers to validate the results. True and false positives are used to refine machine learning algorithms.
    

## Understand alert types

The current alert reference list contains over 500 types of alerts. The reference list can be reviewed at: [Security alerts - a reference guide](https://learn.microsoft.com/en-us/azure/security-center/alerts-reference)

Each alert type has a description, severity, and MITRE ATT&CK tactic

### **MITRE ATT&CK tactics**

Understanding the intention of an attack can help you investigate and report the event more easily. To help with these efforts, Defender for Cloud alerts includes the MITRE tactics with many alerts. The series of steps that describe the progression of a cyberattack from reconnaissance to data exfiltration is often referred to as a "kill chain".

Defender for Cloud's supported kill chain intents are based on version 7 of the MITRE ATT&CK matrix and described in the table below.

| Tactic | Description  |
|---|---|
| PreAttack | PreAttack could be either an attempt to access a certain resource regardless of malicious intent or a failed attempt to gain access to a target system to gather information prior to exploitation. This step is usually detected as an attempt, originating from outside the network, to scan the target system and identify an entry point.  |
| InitialAccess | InitialAccess is the stage where an attacker manages to get a foothold on the attacked resource. This stage is relevant for compute hosts and resources such as user accounts, certificates, etc. Threat actors will often be able to control the resource after this stage.  |
| Persistence | Persistence is any access, action, or configuration change to a system that gives a threat actor a persistent presence on that system. Threat actors will often need to maintain access to systems through interruptions such as system restarts, loss of credentials, or other failures that would require a remote access tool to restart or provide an alternate backdoor for them to regain access.  |
| PrivilegeEscalation | Privilege escalation is the result of actions that allow an adversary to obtain a higher level of permissions on a system or network. Certain tools or actions require a higher level of privilege to work and are likely necessary at many points throughout an operation. User accounts with permissions to access specific systems or perform specific functions necessary for adversaries to achieve their objective may also be considered an escalation of privilege.  |
| DefenseEvasion | Defense evasion consists of techniques an adversary may use to evade detection or avoid other defenses. Sometimes these actions are the same as (or variations of) techniques in other categories that have the added benefit of subverting a particular defense or mitigation.  |
| CredentialAccess | Credential access represents techniques resulting in access to or control over system, domain, or service credentials used within an enterprise environment. Adversaries will likely attempt to obtain legitimate credentials from users or administrator accounts (local system administrator or domain users with administrator access) to use within the network. With sufficient access within a network, an adversary can create accounts for later use within the environment.  |
| Discovery | Discovery consists of techniques that allow the adversary to gain knowledge about the system and internal network. When adversaries gain access to a new system, they must align themselves to what they now have control of and what benefits operating from that system give to their current objective or overall goals during the intrusion. The operating system provides many native tools that aid in this post-compromise information-gathering phase.  |
| LateralMovement | Lateral movement consists of techniques that enable an adversary to access and control remote systems on a network and cloud, but doesn't necessarily, include execution of tools on remote systems. The lateral movement techniques could allow an adversary to gather information from a system without needing more tools, such as a remote access tool. An adversary can use lateral movement for many purposes, including remote Execution of tools, pivoting to more systems, access to specific information or files, access to other credentials, or to cause an effect.  |
| Execution | The execution tactic represents techniques that result in execution of adversary-controlled code on a local or remote system. This tactic is often used with lateral movement to expand access to remote systems on a network.  |
| Collection | Collection consists of techniques used to identify and gather information, such as sensitive files, from a target network prior to exfiltration. This category also covers locations on a system or network where the adversary may look for information to exfiltrate.  |
| Exfiltration | Exfiltration refers to techniques and attributes that result or aid in the adversary removing files and information from a target network. This category also covers locations on a system or network where the adversary may look for information to exfiltrate.  |
| CommandAndControl | The command and control tactic represents how adversaries communicate with systems under their control within a target network.  |
| Impact | Impact events primarily try to directly reduce the availability or integrity of a system, service, or network, including manipulation of data to impact a business or operational process. This would often refer to techniques such as ransomware, defacement, data manipulation, and others. |

# Remediate alerts and automate responses

From Defender for Cloud's overview page, select the Defender for Cloud tab at the top of the page or the link on the sidebar.

![Screenshot of the Defender for Cloud Alerts list page.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/alerts-page.png)

From the Security alerts list, select an alert. A side pane opens and shows a description of the alert and all the affected resources.

![Screenshot of the Defender for Cloud Alert Details Flyout.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/alerts-details-pane.png)

For further information, select View full details.

The left pane of the security alert page shows high-level information regarding the security alert: title, severity, status, activity time, description of the suspicious activity, and the affected resource. Alongside the affected resource, are the Azure tags relevant to the resource. Use tags to infer the organizational context of the resource when investigating the alert.

The right pane includes the Alert details tab containing further details of the alert to help you investigate the issue: IP addresses, files, processes, and more.

![Screenshot of the Defender for Cloud Alert Detail page.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/security-center-alert-remediate.png)

Also in the right pane is the Take action tab. Use this tab to take further actions regarding the security alert. Actions such as:

-   Mitigate the threat - provides manual remediation steps for this security alert
    
-   Prevent future attacks - provides security recommendations to help reduce the attack surface, increase security posture, and thus prevent future attacks
    
-   Trigger automated response - provides the option to trigger a logic app as a response to this security alert
    
-   Suppress similar alerts - provides the option to suppress future alerts with similar characteristics if the alert isn’t relevant for your organization
    

![Screenshot of the Defender for Cloud Alert Take Action tab.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/alert-take-action.png)

## Automate responses

Every security program includes multiple workflows for incident response. These processes might include notifying relevant stakeholders, launching a change management process, and applying specific remediation steps. Security experts recommend that you automate as many steps of those procedures as you can. Automation reduces overhead. It can also improve your security by ensuring the process steps are done quickly, consistently, and according to your predefined requirements.

This feature can trigger Logic Apps on security alerts and recommendations. For example, you might want Defender for Cloud to email a specific user when an alert occurs.

## Create a logic app and define when it should automatically run

From Defender for Cloud's sidebar, select Workflow automation.

From this page, you can create new automation rules and enable, disable, or delete existing ones.

To define a new workflow, select Add workflow automation.

A pane appears with the options for your new automation. Here you can enter:

-   A name and description for the automation.
    
-   The triggers that will initiate this automatic workflow. For example, you might want your Logic App to run when a security alert that contains "SQL" is generated.
    
-   The Logic App that will run when your trigger conditions are met.
    

![Screenshot of the Defender for Cloud Workflow Automation Add a workflow.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/add-workflow.png)

From the Actions section, select Create a new one to begin the Logic App creation process.

You'll be taken to Azure Logic Apps.

-   Enter a name, resource group, and location, and select Create.
    
-   In your new logic app, you can choose from built-in, predefined templates from the security category. Or you can define a custom flow of events to occur when this process is triggered.
    

The logic app designer supports the following Defender for Cloud triggers:

-   When a Defender for Cloud Recommendation is created or triggered - If your logic app relies on a recommendation that gets deprecated or replaced, your automation will stop working. You'll then need to update the trigger. To track changes to recommendations, see Defender for Cloud release notes.
    
-   When a Defender for Cloud Alert is created or triggered - You can customize the trigger so that it relates only to alerts with the severity levels that interest you.
    

![Screenshot of the Logic App U I and a sample logic app.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/sample-logic-app.png)

After you've defined your logic app, return to the workflow automation definition pane ("Add workflow automation"). Select **Refresh** to ensure your new Logic App is available for selection.

Select your logic app and save the automation. The Logic App dropdown only shows Logic Apps with supporting Defender for Cloud connectors mentioned above.

## Manually trigger a logic app

You can also run Logic Apps manually when viewing any security alert or recommendation.

To manually run a Logic App, open an alert or a recommendation and select Trigger Logic App.

# Suppress alerts from Defender for Cloud

The Defender for Cloud plans detect threats in any area of your environment and generate security alerts. When a single alert isn't interesting or relevant, you can manually dismiss it. Alternatively, use the suppression rules feature to automatically dismiss similar alerts in the future. Typically, you'd use a suppression rule to:

-   Suppress alerts that you've identified as false positives
    
-   Suppress alerts that are being triggered too often to be useful
    

Your suppression rules define the criteria for which alerts should be automatically dismissed. Suppression rules can only dismiss alerts that have already been triggered on the selected subscriptions.

## Create a suppression rule

To create a rule directly in the Azure portal:

From Defender for Cloud's security alerts page:

-   Locate the specific alert you don't want to see anymore, and from the ellipsis menu (...) for the alert, select Create suppression rule:

OR

-   select the suppression rules link at the top of the page, and from the suppression rules page select Create new suppression rule:

In the new suppression rule pane, enter the details of your new rule.

-   Your rule can dismiss the alert on all resources so you don't get any alerts like this one in the future.
    
-   Your rule can dismiss the alert on specific criteria - when it relates to a specific IP address, process name, user account, Azure resource, or location.
    

![Screenshot of Defender for Cloud new alert suppression rule pane.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/new-suppression-rule-pane.png)

Enter details of the rule:

-   Name - A name for the rule. Rule names must begin with a letter or a number, be between 2 and 50 characters, and contain no symbols other than dashes (-) or underscores (_).
    
-   State - Enabled or disabled.
    
-   Reason - Select one of the built-in reasons or 'other' if they don't meet your needs.
    
-   Expiration date - An end date and time for the rule. Rules can run for up to six months.
    

Optionally, test the rule using the Simulate button to see how many alerts would have been dismissed if this rule had been active.

Save the rule.

## View suppressed alerts

Alerts that match your enabled suppression rules will still be generated, but their state will be set to dismissed. You can see the state in the Azure portal or however you access your Defender for Cloud security alerts.

Use Defender for Cloud's filter to view alerts that have been dismissed by your rules.

-   From Defender for Cloud's security alerts page, open the filter options, and select **Dismissed**.

# Generate threat intelligence reports

Triaging and investigating security alerts can be time consuming for even the most skilled security analysts. For many, it's hard to know where to begin.

Defender for Cloud uses analytics to connect the information between distinct security alerts. Using these connections, Defender for Cloud can provide a single view of an attack campaign and its related alerts to help you understand the attacker's actions and the affected resources.

Incidents appear on the Security alerts page. Select an incident to view the related alerts and get more information.

On the Defender for Cloud overview page, select the Security alerts tile. The incidents and alerts are listed. Notice that security incidents have a different icon to security alerts.

![Screenshot of Defender for Cloud Incidents in the Alerts page.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/security-center-manage-alerts.png)

To view details, select an incident. The Security incident page shows more details.

![Screenshot of Defender for Cloud Security Alert Incident details.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/incident-details.png)

The left pane of the security incident page shows high-level information about the security incident: title, severity, status, activity time, description, and the affected resource. Next to the affected resource, you can see the relevant Azure tags. Use these tags to infer the organizational context of the resource when investigating the alert.

The right pane includes the Alerts tab with the security alerts that were correlated as part of this incident.

To switch to the Take action tab, select the tab or the button at the bottom of the right pane. Use this tab to take further actions such as:

-   Mitigate the threat - provides manual remediation steps for this security incident
    
-   Prevent future attacks - provides security recommendations to help reduce the attack surface, increase security posture, and prevent future attacks
    
-   Trigger automated response - provides the option to trigger a Logic App as a response to this security incident
    
-   Suppress similar alerts - provides the option to suppress future alerts with similar characteristics if the alert isn’t relevant for your organization
    

To remediate the threats in the incident, follow the remediation steps provided with each alert.

## Generate threat intelligence reports

Defender for Cloud threat protection works by monitoring security information from your Azure resources, the network, and connected partner solutions. It analyzes this information, often correlating information from multiple sources, to identify threats.

When Defender for Cloud identifies a threat, it triggers a security alert containing detailed information regarding the event, including suggestions for remediation. Defender for Cloud provides threat intelligence reports containing information about detected threats to help incident response teams investigate and remediate threats. The report includes information such as:

-   Attacker’s identity or associations (if this information is available)
    
-   Attackers’ objectives
    
-   Current and historical attack campaigns (if this information is available)
    
-   Attackers’ tactics, tools, and procedures
    
-   Associated indicators of compromise (IoC) such as URLs and file hashes
    
-   Victimology, which is the industry and geographic prevalence to assist you in determining if your Azure resources are at risk
    
-   Mitigation and remediation information
    

Defender for Cloud has three types of threat reports, which can vary according to the attack. The reports available are:

-   Activity Group Report: provides deep dives into attackers, their objectives, and tactics.
    
-   Campaign Report: focuses on details of specific attack campaigns.
    
-   Threat Summary Report: covers all of the items in the previous two reports.
    

This type of information is useful during the incident response process, where there's an ongoing investigation to understand the source of the attack, the attacker’s motivations, and what to do to mitigate this issue in the future.

## To access the threat intelligence report

To generate the report:

From Defender for Cloud's sidebar, open the Security alerts page.

Select an alert. The alerts details page opens with more details about the alert. Below is the Ransomware indicators detected alert details page.

![Screenshot of Defender for Cloud ransomware indicators detected link to threat intel report.](https://learn.microsoft.com/en-us/training/wwl-sci/remediate-azure-defender-security-alerts/media/ransomware-indicators-detected-link-to-threat-intel-report.png)

Select the link to the report, and a PDF will open in your default browser.

# Respond to alerts from Azure resources

## Respond to Defender for Cloud for Key Vault alerts

When you receive an alert from Defender for Key Vault, we recommend you investigate and respond to the alert as described below. Defender for Key Vault protects applications and credentials, so even if you're familiar with the application or user that triggered the alert, it's important to verify the situation surrounding every alert.

Every alert from Defender for Key Vault includes the following elements:

-   Object ID
    
-   User Principal Name or IP Address of the suspicious resource
    

### Contact

-   Verify whether the traffic originated from within your Azure tenant. If the key vault firewall is enabled, it's likely that you've provided access to the user or application that triggered this alert.
    
-   If you can't verify the source of the traffic, continue to Step 2. Immediate mitigation.
    
-   If you can identify the source of the traffic in your tenant, contact the user or owner of the application.
    

### Immediate mitigation

If you don't recognize the user or application, or if you think the access shouldn't have been authorized:

-   If the traffic came from an unrecognized IP Address:
    
    -   Enable the Azure Key Vault firewall as described in Configure Azure Key Vault firewalls and virtual networks.
        
    -   Configure the firewall with trusted resources and virtual networks.
        
-   If the source of the alert was an unauthorized application or suspicious user:
    
    -   Open the key vault's access policy settings.
        
    -   Remove the corresponding security principal, or restrict the operations the security principal can perform.
        
-   If the source of the alert has an Azure Active Directory role in your tenant:
    
    -   Contact your administrator.
        
    -   Determine whether there's a need to reduce or revoke Azure Active Directory permissions.
        

### Identify impact

When the impact has been mitigated, investigate the secrets in your key vault that were affected:

1.  Open the “Security” page on your Azure Key Vault and view the triggered alert.
    
2.  Select the specific alert that was triggered. Review the list of the secrets that were accessed and the timestamp.
    
3.  Optionally, if you have key vault diagnostic logs enabled, review the previous operations for the corresponding caller IP, user principal, or object ID.
    

### Take action

When you've compiled your list of the secrets, keys, and certificates that the suspicious user or application accessed, you should immediately rotate those objects.

-   Affected secrets should be disabled or deleted from your key vault.
    
-   If the credentials were used for a specific application:
    
    -   Contact the administrator of the application and ask them to audit their environment for any uses of the compromised credentials since they were compromised.
        
    -   If the compromised credentials were used, the application owner should identify the information that was accessed and mitigate the impact.
        

## Respond to Defender for DNS alerts

When you receive an alert from Defender for DNS, we recommend you investigate and respond to the alert as described below. Defender for DNS protects all connected resources, so even if you're familiar with the application or user that triggered the alert, it's important to verify the situation surrounding every alert.

### Contact

Contact the resource owner to determine whether the behavior was expected or intentional.

-   If the activity is expected, dismiss the alert.
    
-   If the activity is unexpected, treat the resource as potentially compromised and mitigate as described in the next step.
    

### Immediate mitigation

Isolate the resource from the network to prevent lateral movement.

-   Run a full antimalware scan on the resource, following any resulting remediation advice.
    
-   Review installed and running software on the resource, removing any unknown or unwanted packages.
    
-   Revert the machine to a known good state, reinstalling the operating system if necessary, and restore software from a verified malware-free source.
    
-   Resolve any Defender for Cloud recommendations for the machine, remediating highlighted security issues to prevent future breaches.
    

## Respond to Defender for Resource Manager alerts

When you receive an alert from Defender for Resource Manager, we recommend you investigate and respond to the alert as described below. Defender for Resource Manager protects all connected resources, so even if you're familiar with the application or user that triggered the alert, it's important to verify the situation surrounding every alert.

### Contact

Contact the resource owner to determine whether the behavior was expected or intentional.

-   If the activity is expected, dismiss the alert.
    
-   If the activity is unexpected, treat the related user accounts, subscriptions, and virtual machines as compromised and mitigate as described in the following step.
    

### Immediate mitigation

-   Remediate compromised user accounts:
    
    -   If they’re unfamiliar, delete them as they may have been created by a threat actor
        
    -   If they’re familiar, change their authentication credentials
        
    -   Use Azure Activity Logs to review all activities performed by the user and identify any that are suspicious
        
-   Remediate compromised subscriptions:
    
    -   Remove any unfamiliar Runbooks from the compromised automation account
        
    -   Review IAM permissions for the subscription and remove permissions for any unfamiliar user account
        
    -   Review all Azure resources in the subscription and delete any that are unfamiliar
        
    -   Review and investigate any security alerts for the subscription in Defender for Cloud
        
    -   Use Azure Activity Logs to review all activities performed in the subscription and identify any that are suspicious
        
-   Remediate the compromised virtual machines
    
    -   Change the passwords for all users
        
    -   Run a full antimalware scan on the machine
        
    -   Reimage the machines from a malware-free source

# Knowledge check

1. Defender for Cloud employs which advanced security analytics?

Biometric analytics

Power BI

[X] Behavioral analytics

Correct. Behavior analytics is used to detect threats.

2. Which Azure technology is used to automate remediation?

Azure Functions

Azure Batch

[X] Azure Logic Apps

Correct. Logic Apps is the automation engine.

3. If available, which report provides Attackers tactics, tools, and procedures?

[X] Threat Intelligence

Correct. The threat intelligence report contains attacker information if available.

Secure Score

Incident

# Summary and resources

You should have learned how Microsoft Defender for Cloud provides a purpose-driven user interface to manage and investigate security incidents and alerts across protected resources. The alert includes actions to take to remediate the threat and steps to prevent future attacks.

You should now be able to:

-   Describe alerts in Microsoft Defender for Cloud
-   Remediate alerts in Microsoft Defender for Cloud
-   Automate responses in Microsoft Defender for Cloud

## Learn more

You can learn more by reviewing the following.

[Become a Microsoft Defender for Cloud Ninja (microsoft.com)](https://techcommunity.microsoft.com/t5/azure-security-center/become-an-azure-security-center-ninja/ba-p/1608761)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)