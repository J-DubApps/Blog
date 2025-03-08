+++
date = '2025-04-05T01:17:51-06:00'
draft = true
title = 'Introduction to Kanban'
description = ""
type = 'post'
tags = ["kanban", "agile", "project-mgmt", "taskmgmt", "devops", "secops", "enterprise-it", "it-service-mgmt", "work-culture", "intermediate-advanced", "special-write-up", "best-practices", "organizational-transformation", "walkthru"]
+++

APPENDIX II

Agile - Agile is a way of managing and organizing work that focuses on flexibility, collaboration, and continuous improvement.  Agile is traditionall a Project Management process; however we do not use Agile for Projects, but for organizing Tasks and Units of Work for those Tasks.  Agile methodologies, such as Scrum and Lean, are also designed to help people stay focused and manage daily-interruptions, without productivity loss. By using Agile methodologies, a Team can break their work down into smaller, manageable chunks and prioritize those Tasks and sub-tasks based on importance and urgency. This can help a Team stay focused on the most value-aligned and important tasks…while still tracking, and avoid being interrupted by, less urgent Tasks.
 
Alignment -  Alignment refers to the process to verify that a Team's goals or Next Actions are agreed upon during Project work.  Alignment also refers to synchronizing a Team's understanding of a Task at-hand with the Task Stakeholder or the PM, and includes the expected Output / Deliverable and estimated Sprint time toward completion of a Task.   Alignment occurs during Project Meetings,  Backlog  Maintenance Meetings, and in Value-Management.  Any Task that is mis-aligned from current Project or Team goasl, may be Reverted (returned to the BACKLOG).
 
Communication Endpoints (or Channels) -- Members on of any Team (IT Team, DevOps Team, or Project Team) who must be communicated with one-on-one during RCA troubleshooting work or for Project Work Breakdown sessions are individual Comms Endpoints, or Channels.  Kanban helps streamline Task Management Communication between multiple Task Resources (Comms Endpoints) on a Team.
 
A helpful formula used to calculate the number of communication endpoints in a any team (even a small team) is:
 
The formula for calculating the number of communication channels (N) in a project team is:
 
N = n * (n - 1) / 2
 
where "n" represents the number of Team members (on an IT or Project Team, etc).
 
This formula illustrates how communication complexity increases as the team size grows.  The formula demonstrates that as the number of team members increases, the number of communication endpoints increases exponentially, which in turn increases the communication burden on IT Managers, the Project Manager and the Team.
 
Efficient communication management becomes crucial as the team size grows to ensure smooth project execution and closure of ITSM Escalations.  Kanban, by bringing a visual Task Management capability gives Teams the ability to effectively manage their communication.
 
Communication Management -- The processes and techniques employed by members of a Team ensure effective and efficient information exchange among all Task and/or Project Stakeholders in a Task work group.  When the number of Communication Endpoints can rise per Project Team, or during Urgent Task Work, it becomes crucial to have a structured communication approach to maintain clear, concise, and timely information flow. With Task Management and Task Work on the SysOps Team, Kanban enacts a form of Communication Management by requiring clearly defined Tasks ("The Three Things") and holding Daily Stand-Ups and Backlog Maintenance Meetings.
 
Communication Management Plan -- An plan outlining communication needs, methods, frequency, and responsibilities within a Team (or Project Team). Kanban itself enacts a form of Communication Management in addition to Task Management.  A Comms Mgmt Plan can help ensure that all stakeholders receive the necessary information and provides a framework for managing communication channels to avoid Noise overburdening Task Resources
 
Deliverable - is a good or service to be provided at the completion of a Task, aka an OUTPUT.  It's a term usually used in project management, as the scope of a project can often be measured by the deliverables produced during the project run.
 
Float - The term "float" refers to the amount of time that a Task or Deliverable can be delayed or remain incomplete, without impacting or Blocking other dependent Tasks. In other words, float is the amount of time that a task can be "flexible" without affecting an overall Project schedule.  For example, if a task has a float of 2 days, it means that the task can be delayed by up to 2 days without delaying the completion of another Task or Project Deliverable.  In such a scenario, floating a Task requires you to notify the Task Stakeholder and the PM, so that your paused Task does not become a Block. 
 
Focus Factor - The focus factor is a measure of how focused a Team is on a specific set of Tasks or objectives. In Scrum, the focus factor is used to help teams stay focused on their sprint goals and to minimize distractions and interruptions. By focusing on a specific set of tasks and objectives, teams can increase their chances of entering and staying in a state of flow, which can lead to higher productivity and better results.
 
Focus Factor can sometimes be expressed in a mathematical formula for forecasting the number of Task Completions or Deliverables possible in an iteration, based on past completed Task or Deliverables from our past Sprints.
 
Gold Plating -- Gold Plating happens when a Project Stakeholder adds extra features that were not part of the original scope, usually “nice to have" add-ons not envisioned, discussed, or Scoped in the Project's formation and Chartering.  In Kanban Task Management, Gold Plating occurs when the requestor of a Task (Task Stakeholder) revises that Task with "new asks" that change the Task entirely (and should be in a new Task Request for the BACKLOG).  Sometimes a "new ask" contains a request that may not pass Value Analysis that occurs during Value Management discussion in Backlog Maintenance Meetings. 
 
Gold Plating should be avoided and receive proper scrutiny.  It is sometimes possible that the Task Stakeholder did not understand the original problem to solve, hence their additional request (so not Gold Plating but something that may bring value).  So when you suspect Gold Plating, forward the new ask to the Kanban Board Admin so that our PM or IT Managers can review the new Task Request for Gold Plating vs additional Task or Sub-Task creation.
 
INPUT -- any resource, information, or condition that is required to start or perform a project activity.  On the SysOps Team we get Tasks Requests (Candidate Tasks)  from multiple sources that will trigger Task Work activities.  See also SysOps Kanban INPUTs as this is also critical definition to understand in terms of Kanban and SysOps Task work.
 
OUTPUT -- The result, product, or Deliverable generated by completing a project activity (this can be a Work Breakdown Structure (WBS), a Risk Log, or more commonly a Project Deliverable itself).  On the SysOps Team this is also the result of completed Tasks.  See also SysOps Kanban OUTPUTs as this is also critical definition to understand in terms of Kanban SysOps Task work.
 
Project -- A Project is a temporary endeavor undertaken to create a unique product, service or result. A project is temporary in that it has a defined beginning and end in time, and therefore defined scope and resources.
 
Project Deliverable -- simply the results of project activities.  Our Tasks may frequently come from scoped Projects, and the results of our completed Project Tasks (our OUTPUTs) are Deliverables for that Project.
 
Project Manager -- The Project Manager (PM) is the professional on our IT Team who organizes, plans, and executes our Projects while working within restraints like technical resources, budgets, and schedules.  Our IT Project Manager is Larry Taylor, who is also one of our Kanban Board Administrators and one of our available MCs for our weekly Backlog Maintenance Meetings.  Larry also contributed a lot to this Kanban Task Management manual and our evolving DSU process, and we thank him for his help in this area!
 
Project Stakeholder -- Project stakeholders are all Individuals and groups in the organization who are actively involved in the project, or whose interests may be positively or negatively affected as a result of project execution and successful project completion.  Not to be confused with a Task Stakeholder in our Kanban: these are individuals who made a Task Request or created a Task for the SysOps group's BACKLOG.
 
Project Task -- Project Tasks are Units-Of-Work that bear directly on completing a Project Deliverable or set of Deliverables.  Project Tasks may or may not arrive from a Work Breakdown Structure (WBS) Project OUTPUT, but at McKool Smith generally the Systems Operation group will receive defined Tasks directly relating to Project Deliverables.   See Task definition in Kanban terms for a Task Management definition for an individual Task, as well.
 
Risk -- Risk is defined as an uncertain event or set of events that can affect the objectives of a Project or, in our area of Systems Ops, completion of a Task or Unit of Work.  In Task Management a Risk, once identified, may contribute to a Task not being completed on time or with accuracy.  In Project Management Risk is critical because a Risk, once identified, may either contribute to the success or failure of a Project if it is not managed.  Applying Risk Management methodologies will help with Risk, and can also help identify Opportunities as well (e.g. a repeated Risk of missed Timetables with for Task work can result in the Opportunities that Kanban or other Task Management can bring).
 
Risk Log (or Risk Register) -- A tool in Project Risk or ITSM Risk Management which is used to identify, assess, and track risks throughout the lifecycle of a Project or IT system Task Work.  In Project Management, this is a living document that evolves as the project progresses, helping project managers and their teams to proactively manage risks, take appropriate mitigation actions, and develop contingency plans.
 
Scope Creep - Scope creep occurs through uncontrolled changes or expansions to a Project's active Tasks or Project Scope without adjusting the project’s time, cost, or other resources. It usually happens little by little and can create issues in a Project's later stages. Controlling Scope through Value Management in Project and Backlog Maintenance Meetings is a critical feature of Kanban and Agile, Waterfall, and other Project and Task Management methods. 
 
With System Ops team Tasks, Scope is really not something we need to manage, as Scope is a Project related concern; however, if a Task Stakeholder keeps revising or expanding a Task's directive or request (thus entirely changing that Task's desired outcome, or creating Sub-Tasks) this can be considered a form of "Scope Creep" on that Task.  In that scenario, it is appropriate to communicate the Task Request changes to the Kanban Board Admin can assist with the issue.
 
Scrum - Scrum is a specific type of Agile methodology that is used to manage and organize work. It is based on the idea of dividing work into small, manageable chunks called "Sprints." During each sprint, a team works on a specific set of tasks and then assesses their progress at the end of the sprint. This allows teams to be flexible and adaptable, and to make changes and improvements based on feedback and data.  Currently the SysOps team do not hold formal Sprints, only Daily Stand-Ups to plan work on our Individual Tasks.  But we may perform Weekly Sprints in the future, subject  to PM and Manager discretion.
 
Stand-Up or Daily Stand-Up (DSU) -- Stand-Ups are daily meetings where DevOps / Agile teams quickly connect and align on completed and upcoming work. These meetings are brief & quick — deep dives are not allowed, as the meeting is for discussing ongoing Tasks and Tasks for Projects at a high-level.  Most Stand-Ups should only last 15 minutes.  In Stand-Up the Team reviews the Kanban Board's Active Tasks, and discusses issues and addresses Blocks. This meeting helps build Team dynamics, fosters open communication, and helps team members hold themselves and each other accountable on their active Task work.
 
Do not let the simplicity of Stand-ups fool you — they are critical to keeping any Kanban Board or Scrum operation running.  Without DSUs a Kanban board will fail, as It can be easy to slip into a routine of stale "status" updates while Critical Path Task work is missed: the person running the Stand-Up must push for narrow focus on Tasks in play, and keep the Team focused on Task progression across the Kanban Board.  The Daily Stand-Up is about keeping active work and Flow going  on Task work, and is not about Status of Tasks since the Kanban Board itself should be a Task Status indicator.
 
Sprint - A Sprint (or Iteration cycle) is a fixed time-boxed period(typically between one and two weeks long, depending on Team size and the complexity of work), during which a Team works on a specific set of Tasks. This can also be a single Task Owner's Iteration Cycle for a single Task.
 
The goal of the Sprint is to complete a specific amount of work and make progress towards achieving a larger goals in a Project or other IT department initiative.  During each Sprint, the Team works on a prioritized set of Tasks and then assesses their progress at the end of the Sprint.  Sprints are typically structured to be a formalized uninterrupted period of time where Project work or other Task work is completed, usually a week.  Individual Sprints, to complete a key Task or Deliverable, by a single person can occur in a smaller period, usually a day or two.  Sprints are used in Agile methodologies, such as Scrum, to help teams break their work down into smaller, more manageable chunks and to focus on making progress on the most important tasks.
 
User Story - A User Story in agile/ scrum is often used to manage software development Project Tasks; however, in Kanban Task Management a User Story is a tool used to do two things:
 
1. Establish the context or need for a non Project-related Task Request.
2. Represent the smallest unit of work that would result from the Task, if approved during Backlog Triage.
 
User Stories provide an informal, natural language description of a feature of the issue needing addressed from the end-user perspective.  User Stories help us apply Value Management to determine if a Task should proceed from the BACKLOG. 
 
We do not always have, or need, a User Story to proceed with Assigning a Task to a Task Owner.  It is simply additional information that provides us added-value.
 
Value --  "Value" refers to the worth or importance that is placed on a Service, a Task, or related Deliverable - and typically in relation to a particular goal or objective (e.g. the System Operations Team mission, a Project, etc).  It can be subjective, and different to each Team member, therefore as a Team we want to always discuss the value of a Task at our Backlog Maintenance Meetings - when working to adjust priorities.
 
In the context of Kanban in DevOps, the "Value" of a Task in the BACKLOG must be evaluated and established (with a Task Priority assigned) before that Task can enter any other Lane!  If you are self-entering a Task on the BACKLOG, you must already have an understood Priority for that Task -- but also be ready to Hold or Swarm on that Task based on it’s the Value of that Task (which can be increased or decreased based on feedback during our Daily Stand-Up).  Self-entered Tasks to ourselves are permitted only if it Aligns with our Value Management (see below) or the Kanban Board Administrator could be instructed to Revert (de-assign, and re-BACKLOG or Delete) your Task!
 
In the Context of Project Management, which is a primary INPUT to our Kanban Board,  "Value" may be defined as the benefits or outcomes that the project or product is intended to deliver to Project Stakeholders.  The Value is already "baked-in" to an active Project, and so doesn’t need to be analyzed in BMMs.
 
Value can be measured in a variety of ways, depending on the Context and the Stakeholders' needs and expectations. For example, Value may be measured in terms of ROI, user satisfaction, operational efficiency, or other impact.
 
Value Management - On the SysOps team, the Value of a Task (especially informal requests from email or meeting conversations, or Tasks without a Directive) is always evaluated in relation to the IT Team's overall mission and responsibilities.  Therefore, the Kanban Board Admin (in concert with the PM and IT Managers) works to constantly review-and-manage Task Priority & Assignments so that they Align with the Values of company strategy, our IT Mission, and active Projects.
 
Value Management is a systematic process used to optimize the Value of a Task, a Project, or Deliverables thereof -- for the benefit of all company Project Stakeholders and the IT Department.  Value Management involves identifying, analyzing, and prioritizing the various elements that contribute Value -- and then make decisions about how to optimize the Value of each element as they relate to approved Units of Work, or Tasks.
 
Value Management typically involves discussions in our Backlog Maintenance Meetings and Project Meetings, where a Task will be prioritized or de-prioritized.  In the Context of Project Management, Value Management involves activities to define a Project's scope and objectives.  It also involves identifying the stakeholders and their needs and expectations, and analyzing the various Value drivers.  The results of these activities are then used by the PM and Project team's decision-making and helps them optimize the Value of a Project and its Tasks and Deliverables. 
 
Any SysOps Task unable to stand up to the IT Team's scrutiny and Value Management activities during Backlog Maintenance Meetings, is considered Gold-Plating or (worse) Scope Creep and can be removed from our Kanban Board by the Board Admin, the PM,  or IT Manager for further review and evaluation of Value drivers.
 
Work Breakdown Session -- A meeting between Project Stakeholders which includes the PM, SMEs, and any other Task Resources where upcoming Task work is defined and estimated and then connected to the known Deliverable OUTPUTS for the purpose of aligning Project Work with the Project Timetable.  At the end of such a meeting, part or all of a Work Breakdown Structure (WBS) may be created as an OUTPUT of this meeting session.
 
Work Breakdown Structure (WBS) -- A WBS in project management and systems engineering is a deliverable-oriented ist of Task Work into smaller components (Individual Tasks and Sub-Tasks).  A WBS is not always needed or feasible on medium and small Projects, but in a Task Mgmt System like Kanban often is.  Any basic WBS will make Task Work plannable and schedulable -- which makes Project and Kanban timetables more manageable and predictable.
 
REMEMBER:  WBS or not -- a Task with a clear Request or Directive (or a Task containing a clear Problem Description and/or a Project Deliverable tied to that Task) will always move into the Kanban Board's IN PROGRESS Status Lanes quickly, requiring little to no discussion in a Backlog Maintenance Meeting or Value Analysis and Mgmt sessions.