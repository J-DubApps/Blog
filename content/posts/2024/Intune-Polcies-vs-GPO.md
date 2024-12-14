+++
date = '2024-11-02T11:15:51-06:00'
draft = false
title = 'Intune Policies: A Primer for GPO Admins'
type = 'post'
tags = ["tech", "microsoft", "intune-csp-gpo", "intune", "enterprise-it", "ms-config-mgr"]
+++

 <style>
        .truncate {
            width: 300px; /* Set the desired width */
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .truncate a {
            text-decoration: none;
            color: blue;
        }
</style>

For AD shops that are in a configuration where their Windows Device endpoints are sync'ed to Entra ID / Azure, there's an area of Intune that will (eventually) become relevant to you if you plan on leveraging Intune to manage them (and you should). <br />

When it comes to Intune and managing Windows Devices, a lot of digital ink has been spilled about Remediation Scripts, Autopilot, and App Depolyment/Updates in Intune -- to name just a few of popular Intune topics. But not nearly enough digital ink has been directed at Intune Configuration Service Providers (CSPs).  And even less write-ups on why GPO admins really need to start getting schooled on this as more hybrid environments will be slowly moving endpoint policy mgmt away from GPO. <br /> 

For some AD shops, Intune is still just an MDM thing (bad, bad place to be for any ConfigMgr shopts: we're early days but Intune is eating the Endpoint Mgmt world...).   So it's understandable that some systems admins and ops groups have not spent a lot of time exploring how Intune can manage configuration policies for Windows endpoints and M365 Apps.  <br /> 

So this blog post is directed at those AD admins and engineers who have only mostly done a little with Intune, but are still probably running Configuration Manager or other on-prem endpoint management solution.  I want to provide those people an Intune CSP primer for them that uses their GPO knowledge to understand this part of Intune.  Because there where virtually no write-ups like this for me, when I had to start learning to apply feature of Intune. <br />


Intune Configuration Service Providers (CSPs) are the most comparable component to Group Policy Objects (GPOs), and here’s a detailed comparison: <br />

Intune CSPs and GPOs <br />
1.	**Definition**: <br />
	•	CSPs: Configuration Service Providers define how management tasks and policies are applied to Windows devices via MDM (Mobile Device Management). They map to registry settings, policies, or configurations in the OS.<br />
	•	GPOs: Group Policy Objects are used in Active Directory to enforce policies and settings for users and devices, based on a domain-joined environment.<br />
2.	**Scope and Application**:<br />
	•	CSPs: Intune CSPs use a cloud-based approach to apply configurations to Azure AD-joined or Hybrid AD-joined devices via MDM channels. They are designed to be device-agnostic and manage configurations through supported MDM protocols.<br />
	•	GPOs: GPOs are applied through an on-prem AD infrastructure and target devices or users based on Active Directory structure (OUs, groups, etc.).
3.	**Feature Set**:<br />
	•	CSPs and GPOs overlap in many areas (e.g., security settings, password policies, app management, network settings).<br />
	•	However, some traditional GPO features (like advanced user configuration) may not yet have direct CSP equivalents.<br />
	•	Microsoft has added Administrative Templates in Intune, which mimic GPO-style settings, enabling easier transition for organizations moving from GPO to Intune.<br />
4.	**Delivery Mechanism**:<br />
	•	CSPs: Delivered via MDM through XML-based policies in Intune.<br />
	•	GPOs: Delivered via the AD domain and processed during computer/user policy refresh.<br />
5.	**Examples of CSP Usage**:<br />
	•	Configuring Windows Update for Business.<br />
	•	Enforcing BitLocker encryption.<br />
	•	Setting device restrictions, such as disabling USB ports.<br />

Other Intune Policy Mechanisms<br />

While CSPs are the direct comparison to GPOs, Intune has additional policy tools that complement and sometimes overlap with CSPs:<br />
1. **Device Configuration Profiles**:<br />
	•	Leverage CSPs under the hood but are presented in a more user-friendly interface within the Intune admin portal.<br />
	•	Can include settings like password policies, VPN configurations, and Wi-Fi profiles.<br />
2. **Administrative Templates**:<br />
	•	Intune’s implementation of traditional GPO settings for specific Windows configurations, like Office settings.<br />
3. **Compliance Policies**:<br />
	•	Define rules and settings that devices must comply with to be considered compliant (e.g., requiring PIN, enforcing encryption).<br />
4. **Endpoint Security Policies**:<br />
	•	Focus on security-centric configurations, such as antivirus settings, firewall rules, and disk encryption.<br />

Comparing GPOs and Intune CSPs 


| **Feature**   | **GPOs**                              |   **Intune CSPs**                     |
|---------------|---------------------------------------|---------------------------------------|
| Delivery      | Domain-based                          |   Cloud-based (MDM)                   |   
| Targeting     | OUs, AD groups                        |   Entra ID / Azure AD groups          |
| Granularity   | Comprehensive                         |  Still expanding, with gaps           |
| Customization | Extensive (via custom ADMX)           |  Limited to supported CSPs            |
| Dependencies	| Requires on-prem AD, network access   |	Requires Azure AD, internet access  |

**When to Use Each** <br />
	•	Use GPOs when managing on-prem, domain-joined devices in a traditional AD infrastructure.
	•	Use Intune CSPs for modern management scenarios with cloud-first, Azure AD-joined devices.

Migration from GPO to Intune CSPs

Microsoft provides tools like the Group Policy Analytics tool in Intune to assess your GPOs and determine their CSP equivalents, facilitating a smoother transition.

I hope this helped clear up any AD/GPO-centric blind spots that may exist for some hybrid Azure / Entra ID admins out there still doing AD-based admninistration of your Windows endpoints.  Becuase it's very likely the day will come when even GPOs are going to start to move towards Intune - yes, even for Windows endpoints that aren't native cloud.  And here's why:  Intune CSPs can apply to endpoints up to 70% *faster* than your AD domain-based GPOs.  That kind of performance-improvment for configuration policies is just too much of a low-hanging fruit *not* to get busy learning about Intune CSPs, and how you can benefit from them in the future!  <br />

Some resources I recommend, for further reading about Intune CSPs and other Intune-related stuff: <br />

