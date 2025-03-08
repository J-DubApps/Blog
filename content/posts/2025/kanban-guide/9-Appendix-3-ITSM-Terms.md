+++
date = '2025-04-05T01:17:51-06:00'
draft = true
title = 'Introduction to Kanban'
description = ""
type = 'post'
tags = ["kanban", "agile", "project-mgmt", "taskmgmt", "devops", "secops", "enterprise-it", "it-service-mgmt", "work-culture", "intermediate-advanced", "special-write-up", "best-practices", "organizational-transformation", "walkthru"]
+++

APPENDIX III

System Ops Kanban Process Terminology & Definitions --
 
ITSM Terms & Concepts
 
ITSM -- Stands for IT Service Management.  Helpdesks / Service Desks and IT Operations teams leverage ITSM tools to track Assets and resolve User and systems issues that are detected or reported (ITSM Tickets).  The McKool Smith SysOps team takes Escalations from the Service Desk , and we normally only work them outside of our Kanban Board unless such Escalations need to be broken down into Tasks to resolve the user's issue and close the Escalation Ticket.  Never place Tasks arising from Escalation Tickets into our BACKLOG Lane of our Kanban Board!  Escalations Tasks, depending on their urgency, go into the IN PROGRESS Lane or EMERGENCY Lane only.
 
Change  - A "Change" (or Change Event) pertains to Change Management, when any modification or update to an IT system or its components, such as hardware or software, takes place.  This can include anything from installing a new piece of software, to upgrading hardware, to even changing the way something is done by the team. is carried out. A change event can be planned or unplanned, and can range in scope from a minor update to a major overhaul of the system.
 
Change Management - Change management is the process of identifying, planning, and implementing changes to enterprise IT systems in a controlled and coordinated way. The goal of change management is to minimize disruptions to the organization and its employees, and to ensure that changes are implemented in a consistent and effective manner. This typically involves developing policies and procedures for handling changes, as well as training employees on how to properly implement and manage changes to the system.  This process may also involve a CAB or, at minimum, Peer-Review (where another SME on the Team will co-sign or endorse "+1" the proposed Change for consideration and Approval).
 
Change Advisory Board (CAB) --  Also called a Change Control Board (CCB).  This is a structured and formalized group that reviews and approves or declines proposed Changes to an IT environment (Infrastructure Changes or other software or hardware  configuration Changes).
 
Downtime Event - A period during which all or a portion of an IT system was unavailable to provide End-User or related services.  This includes planned (via Change Management) or unplanned Downtime.
 
Endpoint - Any device, managed or unmanaged, where an End User performs work and creates Work Product for McKool Smith.  While the firm prefers work be performed on managed Endpoints, there are no policies against performing work on personal or "BYOD" devices that are not firm-owned.  One goal of Endpoint Management (defined below) is to bring at least minimal controls or management to All Endpoints even if not firm-owned. 
 
Endpoint Configuration Management -- An IT Operations, and Systems Operations, focus that involves tooling (Currently Track-It and MECM) and processes (Change Management, QA/QC processes) to deploy, track, and manage user PCs (also called Workstations, or Endpoints).
 
Knowledge Worker -- Knowledge Workers are anyone and everyone on the IT Team who supports our mission, troubleshoots problems, and contributes to our teamwork dealing with various technologies at McKool Smith.  Knowledge Workers are: Us!  Each member of the Mckool Smith IT Staff is a Knowledge Worker and thus a Task Resource that can, at times, assist in ITSM Ticket and Kanban Task work.  Some Knowledge Worker Resources may possess specialized skills or experience, and we refer to those Resources as an SME for certain specialized Tasks.  See also SME below.  
 
MSP - Managed Service Provider.   A third-party company or vendor that remotely manages IT Services, and may also provide assistance during Projects (including and up to staff augmentation during critical projects).
 
Operations -- This includes the Service Desk, our Endpoint Support Technicians, and our Systems Operations team.
 
Peer-Review -- In IT, and also Kanban and Agile, this is when you may get a colleague (e.g. The Kanban Board Admin ) to endorse, or co-sign ("+1")  something like an Agile Task Request.  In Change Management, where there is no CAB or CCB, a Team's SMEs or Managers may review and endorse (co-sign) a Change or scheduled Change Event.  This procedure contrasts with Traditional Change Management, where a CAB and other processes are  used to Approve a Change.  "Agile Change Management" or "Lightweight Change Management" are newer areas of Change Management that do not require the CAB apparatus.  However, environments with frequent complex changes may not be best-served by newer Change Management methodologies.
 
QA / QC - Quality assurance and quality control are two closely related concepts that are often used in the context of evaluating the quality of a product or service after a Change Event (such as deploying new software to a group of early adopting Pilot Users, and soliciting feedback).
 
Quality assurance refers to the overall process of ensuring that a product or service meets certain standards of quality. This can include activities such as developing and implementing quality control policies, training employees on quality standards, and carrying out regular inspections and audits to ensure that the product or service meets the required standards.
 
Quality control, on the other hand, is the specific processes used to evaluate a product or service to determine whether it meets the required standards of quality.  This can include activities such as testing the product or service to ensure that it functions properly, checking it for defects or other issues, and comparing it to established quality standards.
 
Together, quality assurance and quality control form a comprehensive approach to evaluating the quality of a product or service after a Change Event.  By implementing quality assurance processes and carrying out quality control evaluations, organizations can ensure that changes to their systems are implemented in a way that maintains or improves the overall quality of their products or services.
 
RCA - Root Cause Analysis. Problem-solving method and activity that IT Staff and Engineers engage in daily. RCA is used by the SysOps team to identify the underlying or fundamental cause of an issue or problem.  Often RCA work is driven by a Service Desk Escalation, discovered issues during a Change, or as part of a post-outage review.  RCA is also used to identify the underlying causes of system failures or performance issues. The goal of RCA is always to identify the root cause of the problem, rather than just repeatedly treating the symptoms, in order to prevent the issue from happening again in the future. This can involve collecting and analyzing data, identifying patterns and trends, and conducting tests or simulations to determine the underlying cause of a problem. By identifying the root cause of a problem, DevOps and Systems Operation engineers can take steps to fix an issue permanently.  Kanban processes aid in RCA Tasks and planned activities, since some RCA activities can last several days and be subject to multiple Interruptions and Pivots.
 
Risk Management -- Refers to the systematic process of identifying, assessing, and mitigating risks associated with changes to IT services and infrastructure. The goal is to minimize potential negative impacts on service delivery, maintain the stability of the IT environment, and ensure that changes are introduced in a controlled and efficient manner.  Also may refer to the process of identifying and managing Risks to a Project.
 
SME - Subject Matter Expert, basically the person who best experienced and suited for the Task entered on the board.  Tasks may be assigned to a group with limited staff resources, where only a few (or even a single) staffers can complete a Task or Sub-Task.  In Kanban, you employ WIP Limits and monitoring to ensure that the correct SME is matched to a Task or Sub-Task to avoid unneeded delays. 
 
Service -- A service is a means of delivering value to customers by facilitating outcomes that customers want to achieve, without the ownership of specific costs and risks.  Services can also be internal, whereby a company department or division provides services to employees (e.g. IT Dept and End-Users). 
 
Service Desk -- The Service Desk (previously known as the Helpdesk) is the single point of contact, or SPOC, between the IT department and McKool Smith users. Your typical service desk manages tracking and resolution of incidents and/or service disruptions.  It provides help and solutions for our users in the form of expertise, Endpoint technician resources, and Escalations to our SysOps team. The Service Desk leverages ITSM service management tools to handles service requests or regular service-related tasks.
 
Service Level Agreement (SLA) -- An SLA is a contract between a Service Provider and its customers that documents what services the provider will furnish and defines the service standards the provider is obligated to meet.  An company may maintain internal SLAs for IT and/or other departments for IT Service and System Availability.  Other times a company will instead maintain a Service-Level Commitment (SLC) instead of an SLA for internal IT-managed systems and services.
 
An SLA differs from a Service-Level Commitment which is a broader and more generalized form of an SLA. The two differ because an SLA is bidirectional and involves two teams communicating. In contrast, an SLC is a single-directional obligation that establishes what a team can guarantee its customers at any given time.  Also, SLAs between a Service Provider and customer contain a punitive fine or credit system, for times where an SLA's service parameters are not met.
 
Service Provider -- Any organization supplying Services to one or more Internal or External Customers.  IT Service Providers may provide managed infrastructure services (MSP) or communications services (ISP) or Hosting and other Cloud services (SaaS, IaaS, etc).
 
Single Point of Contact (SPOC) -- is the one person or entity directly responsible for requests and inquiries on ITSM Tickets, Tasks, or Project Deliverable status or other related information.  With Task work, the SysOps team considers the Task Owner to be the SPOC (or Directly Responsible Individual / DRI) for their Assigned Task.  For Project Deliverable tracking, this is our IT PM.  For Project Deliverable Task work, this is the Task Owner.
 
Vendor - A vendor is usually the last entity in the chain of IT Technologies or Products that sells directly to end users or through a channel.  Vendors may also provide implementation services for Projects relating to IT Technologies or Products.