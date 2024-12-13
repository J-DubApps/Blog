+++
date = '2024-12-02T14:15:51-06:00'
draft = false
title = 'Microsoft Forcing Migration to New Outlook in January'
type = 'post'
tags = ["tech", "links", "microsoft", "ms-office", "outlook", "regitry", "intune-csp-gpo", "intune", "enterprise-it", "powershell"]
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

Word erupted back in November that Microsoft would be migrating businesses to the New Outlook client, and the community is responding with Intune remediation scripts, GPO entries (for hybrid "AD-first" endpoints), and Microsoft itself has added new entries within Intune CSPs targeting 365 App config.  <br />

I see most shops that are "registry-first", or still leveraging Group Policies primarily, and so for them I recommend [this article for controlling/managing it](https://borncity.com/win/2024/11/08/migration-from-outlook-classic-to-new-outlook-starts-for-business-customers-at-the-beginning-of-2025/).  <br />


Here is a (new/untested, do *NOT* run in your production environment without sandbox testing first!) [Intune Remediation Script](https://github.com/imabdk/Proactive-Remediations/blob/main/Detect-Remediate-Disable-Prevent-New-Outlook.ps1) which seems a perfect fit to manage/avoid any surpises on your Endpoints.  And the author Martin Bengtsson has a great blog post to accompany it, <a href="https://www.imab.dk/prevent-users-from-switching-and-migrating-to-new-outlook-using-powershell-and-microsoft-intune/">here</a>.<br />

As for the Outlook Web app, it will also migrate users on the web side of things if you don't set a web mailbox policy to also manage it.  More information on that on a MS post [here](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/enable-disable-employee-access-new-outlook#use-outlook-on-the-web-mailbox-policies-to-enable-or-disable-the-new-outlook-for-windows-for-multiple-mailboxes), and it includes tenant PS cmds to set that afforementioned web mailbox policy.  <br />

For my employer or any clients, I would recommend slowly rolling this out with the Outlook Web app first, and then the rest in slow groups.  Especially if you're running the Semi-Annual Channel (SAC), as you'll have more time to test/manage deployment of the new Outllok.<br />

Good luck!