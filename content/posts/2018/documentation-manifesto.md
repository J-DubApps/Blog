+++
date = '2018-06-02T20:10:26-06:00'
draft = false
title = 'My Approach To Documentation'
description = 'Why IT Docs Should Stick to the “WHERE” and the “WHAT”—and Avoid the “WHY” or the “HOW”'
type = 'post'
tags = ["tech", "devops", "best-practice", "enterprise-it", "opinion", "project-mgmt", "thought", "best-of", "beginner-fundamentals", "leadership"]
+++
**In a busy IT environment, *speed and clarity* are** ***everything***. When it comes to internal IT documentation, the *best practice* is to keep it short, sweet, and *accurate*—focusing on the location of systems (“***WHERE***”) and the function they serve (“***WHAT***”). Including detailed explanations of the “***WHY***” behind a setup or the step-by-step “***HOW***” to do something -- within a single KB or documenation system --- will turn your documentation into a sprawling novel that is difficult to maintain! ***More importantly***, **it dilutes the primary mission of documentation: to guide you (or your team) quickly to just the facts**.

### 1. The Purpose of IT Documentation: The “*WHERE*” and the “*WHAT*”
•	**WHERE**: At its core, documentation should identify where a particular resource, server, or system resides. This might include which datacenter, which network segment, or which cloud region. Pinpointing the exact location (or location path) is the first thing your colleagues or future administrators will look for. If a database is moved, or an application is changed, documentation that succinctly captures its new coordinates is invaluable. <br /><br />
•	**WHAT**: Just as important is documenting what a system does. Is this server your primary domain controller, your file server for a particular department, or the home of your mail relay? The brief description of its role or function ensures that anyone scanning the documentation knows immediately why that system matters to the environment—and can either proceed with confidence or hand off the task to the correct team. <br />

By zeroing-in on the “WHERE” and the “WHAT,” you create a handy reference that quickly orients your colleagues to the correct environment or component: <br />

>System Name: **APP-SVR01** (10.99.100.20 /24) <br />
>•	Where: On-premises, Datacenter Rack A, Row 3, Slot 14 <br />
>•	What: Runs Department A’s intranet application (handles internal user authentication & front-end web service) <br />

>System Name: **SQL-PRD02** (192.168.30.5 /24) <br />
>•	Where: Azure East US Region, Resource Group: ProdSQLGroup <br />
>•	What: Primary production SQL server for the Financials database (central transactional DB for billing and invoicing) <br />

>System Name: **FS-ARCHIVE** (172.16.35.24 /16)
>•	Where: On-premises, Datacenter Rack B, Row 2, Slot 5
>•	What: File server hosting long-term archival documents (read-only shared folders for old project data) <br />

<div style="text-align: center; font-size: 10px;"><i>An example of effective System Documentation.  No "Why" or "How" is included here. </i></div><br />


### 2. Why Skip the “*WHY*” in Documentation?
•   **Avoid Extra Complexity**: Documenting the rationale (“WHY”) behind an IT architecture or process can become a rabbit hole of organizational or historical context. While the reasoning might be interesting or even helpful for training, it can easily bog down the documentation. <br /><br />
•	**Maintain Relevance**: Over time, the original “WHY” might lose significance. Mergers, acquisitions, reorganizations, or technology refreshes can alter the big-picture reasoning behind a setup. If your documentation hinges on the “WHY,” it risks becoming outdated quickly. <br /><br />
•	**Prevent Document Bloat**: Extensive background details can stretch your documentation into unwieldy text that obscures the actual references people need. Maintaining a lean approach reduces the burden on whoever updates the docs next. <br />

If your team truly needs to preserve institutional knowledge or ***the story*** behind certain choices and decision, consider storing *that info* in a separate knowledgebase or a wiki specifically dedicated to historical or design decisions. It shouldn’t clutter day-to-day system doc references!

### 4. How to Handle the “*WHY*” and “*HOW*” Elsewhere

*Of course* the “***WHY***” and “***HOW***” *do matter* in an IT organization! But these details are best expressed through: <br />
•	**Design Documents & Project (or PMO) Documentatin**: For large-scale projects or new implementations, a separate architectural or design document helps preserve the context, rationale, and detailed migration steps. These living documents cater to architects, senior engineers, or project teams. <br />
•	**Runbooks / Standard Operating Procedures (SOPs)**: These are short, operational guides for day-to-day tasks, risk mitigation, or disaster recovery. They’re separate from higher-level references and are only relevant to those performing the procedures. <br />
•	**Cross-Training / Mentoring Sessions**: Hands-on demonstrations, workshops, or mentorship sessions that help bridge the skills gap and walk individuals through complex tasks. <br />

By separating the “WHY” and the “HOW” from your high-level documentation, you maintain clarity in each resource type—ensuring that no single resource tries to be everything to everyone.

### 5. The Benefits of *Lean Documentation*
•	**Speed**: Technicians can find the location and purpose of a system within seconds—no scrolling through irrelevant text. <br /> <br />
•	**Maintenance**: It’s easier to keep short references up to date than pages of instructions. <br /> <br />
•	**Consistency**: A consistent format—“WHERE” + “WHAT”—helps your team know exactly what to expect from every document. <br /> <br />
•	**Scalability**: As your environment grows, your documentation methodology remains the same. It’s simply a matter of adding a new entry for each resource or system. <br />

Ultimately, having a single “***source of truth***” that is *uncluttered by tutorials* or historical footnotes ensures a streamlined approach to your IT team's documentation.

## tl;dr: *WHAT YOU SHOULD TAKE FRRM THE CONTENTS ABOVE*

**IT documentation should *never* be a maze of design justifications and step-by-step how-tos**. Instead, keep it plain, direct, and *readable* (almost *scannable* for your [SMEs](https://en.wikipedia.org/wiki/Subject-matter_expert) on staff!). By focusing on the “***WHERE***” (location) and the “***WHAT***” (function), you ensure your documentation remains precise, relevant, and easy to update. Let deeper context or procedural guides live in *separate places*—perfect for training and reference needs! As your environment evolves, you’ll be glad you took this lean approach from the start. 

### *Happy Documenting*!! 😉