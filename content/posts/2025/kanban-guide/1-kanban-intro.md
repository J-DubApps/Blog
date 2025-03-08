+++
date = '2025-04-05T01:17:51-06:00'
draft = true
title = 'Introduction to Kanban'
description = ""
type = 'post'
tags = ["kanban", "agile", "project-mgmt", "taskmgmt", "devops", "secops", "enterprise-it", "it-service-mgmt", "work-culture", "intermediate-advanced", "special-write-up", "best-practices", "organizational-transformation", "walkthru"]
+++

In Manufacturing and Technology professions, Kanban was usually a Project Management tool; however, in DevOps it is generally leveraged as a Task Management tool.  For the remainder of this Guide: Kanban processes shown here are solely as a Task Management System.
 
Workflow on RCA (Root Cause Analysis) and Systems Operations often vastly differs from standard ITSM Operations.  It is not all break/fix, and Engineers tend to receive directives and requests that are not always Event-driven or ITSM Ticket-driven (see INPUTS later in this guide), while other requests are traditional Escalations (Support Incidents, downtime events, etc) and therefore not all work on DevOps or System Ops is simple "1-2-3" and done Units of Work: often Testing & Iteration cycles are required to get to "done" when completing engineering or project related Tasks.
 
Also sometimes a single Task may have several Sub-Tasks that do not lend themselves to description within a single ITSM ticket.  Further, email communications on Actionable Items can be lost in the noise of day-to-day IT operations.  Therefore, a Task Management system that works in-concert with our ITSM is helpful. Enter Kanban (again 😁).
 
When our work does not involve traditional Support Incidents or break/fix style Escalations: we mange our Work Assignments as Tasks using Kanban combined with a few fundamental Agile methods. 
 
Our work often involves Tasks that pertain to maintenance of our back-office technology and infrastructure, and systems management (routine upgrades and security updates).  Tasks may also represent work relating to Change Events (Change Management), and completing Project Tasks (See: Four Task Types that we commonly work on).
 
While sometimes our work can be managed in an ITSM Ticket, many other times they cannot.  Therefore the SysOps team uses our Kanban board to leverage certain Agile and DevOps principles to track our daily work and Project Tasks. 
 
We currently use Microsoft Planner as our Kanban tool*, integrated with our MS Teams Site; however, the Guidelines in this Manual are designed to work with any digital Task-Management tool compatible with Lanes and Agile principles.
 
* We are always evaluating other digital Kanban systems, so try to not fixate on specific tools mentioned in this Guide: our Kanban process is designed to be used with any tool be it digital or even a chalkboard or corkboard.  The prime goal of this Guide is about process over tools.  Strategic over Tactical.
 
Only Tasks that involve Work Product pertaining to specific needs of our Service Desk, our PM, or IT Managers go on our Kanban board.  Tasks may also be focused on a range of day-to-day responsibilities including Software Lifecycle Updates or Deployments, management of McKool Smith's back-office tech infrastructure & systems, which are often standard maintenance activities that may not always be represented as Tasks on the Kanban board.  Yet we often will place complex Network or System Change Event Tasks, Cloud Tenant Change Requests, and similar Tasks onto our Kanban board to track. 
 
Downtime Incidents may also be managed on the Kanban Board as a Task in the EMERGENCY Lane (more on that later in this Guide); however, Tasks in this Lane should also be attached to an ITSM Ticket since such a Task involves a user-impacting event that our Service Desk needs to track. 
Two VERY important things to keep in mind:
 
1. Our Kanban Board is not a Project Management system:  Tasks only!  The board gets its INPUTS (Tasks) from multiple paths including Project Task assignments from our PM, Service Desk ticket Escalations needing Task work, and IT Manager Directives.  We also sometimes will transform informal verbal Directives into Documented Tasks Requests (e.g. "I need X or Y" done) , so that Backlog Triage (and Value Analysis) can be performed. The board generates its OUTPUTS (Completed Tasks) from the work of the Team which includes our SysOps team and greater IT team who helps us complete Tasks and Sub-Tasks.
 
1. The Kanban board is not a work-ticketing system (e.g. Track-IT,  Jira, ServiceNow, etc.):  The SysOps Kanban is simply Task tracking and management tool used in concert with our ITSM.  While ITSM Tickets can be related to Tasks on our Kanban board, Tasks are not Tickets but defined Units-of-Work that are assigned to Task Owners. Tasks come from our BACKLOG, which receives INPUTs from a variety of sources which includes ITSM Tickets.  It is important to understand that, while a Task's status can be ascertained from our Kanban board, the design and intent of our Kanban Board is to allow our small team to juggle multiple Tasks, and allow room for "Flow" (focused work) and productivity to happen efficiently.
 
We are not reviewed, rated, or judged on how many Tasks we create or close per day, on the Kanban Board.
 
 Let me repeat that:  we do not measure our Team's value solely from Tasks closed on our Kanban board.  We measure our value in quality-of-work, internal SLAs, and uptime all of which can only be achieved through sane effective Task Management. 
 
Since our work is only partially "break/fix" ITSM Ticket work, our other Units of Work are performed in Tasks each day pertaining to other classes of work.  Our Task Management system allows for Tasks that contain such long-form work, to take place while managing shifting priorities.  Our day-to-day work involves Testing Desired State Configuration (DSC) of Endpoint PCs (via GPO and Logon Script), documentation of various Systems, and of course day-to-day Systems Management and System Operations.  None-of-which are ITSM related, and all-of-which service "The Ongoing Project of IT Systems Operations".   Enter Kanban.
 
Such work does not always land on the Kanban board: so it is important to understand that our Kanban board's main purpose is to help us manage human generated requests (Tasks, Escalations, etc) and balance it with routine Systems Management activities.  Having a Kanban board allows a place for us to track our BACKLOG of requests (Tasks not yet in Active work) and to rescue our Task Tracking from email, chat, or other comms medium.  Kanban also allows us to manage the Four largest threats to Flow (timely Task work and completion).
 
Our Kanban board is a tool to track Task INPUTS (Requests, Project Tasks, Escalations etc) that come to our team.  This tool exists so that Tasks are not dropped or abandoned, or lost in the day-to-day "noise" of comms, meetings, and shifting priorities. 
 
Our Incoming Task BACKLOG is populated by the following INPUTS: our (upcoming) Change Management System, Service Desk Escalations, Project Management task-assignments, or an IT Manager. 
 
Some Tasks may even enter the BACKLOG Lane after a simple conversation with a coworker (a low-priority, or even zero priority, Task).  Such organic and informal comms will still generate "asks" and thus Tasks, from time-to-time.  So when a Task arises from such interactions, they are documented into the BACKLOG -- even if we do not anticipate working on that Task anytime soon -- for review in the next Backlog Maintenance Meetup (BMM).   Such impromptu discussion Task items have a way of becoming formal Tasks, quickly, so best to get them into the BACKLOG immediately, where they can be sorted and prioritized (or frozen or discarded) later.
 
Completed Tasks are our Kanban board's OUTPUT.  In any given period, while our Kanban board OUTPUTS are  not our only "metric" of Value we provide, this Kanban board exists for SysOps team and our co-workers to keep a daily track of Active Tasks to help the team get our WIP (Work-In-Progress) Tasks completed based on Priority and/or Due Date.