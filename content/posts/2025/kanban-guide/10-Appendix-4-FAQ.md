+++
date = '2025-04-05T01:17:51-06:00'
draft = true
title = 'Introduction to Kanban'
description = ""
type = 'post'
tags = ["kanban", "agile", "project-mgmt", "taskmgmt", "devops", "secops", "enterprise-it", "it-service-mgmt", "work-culture", "intermediate-advanced", "special-write-up", "best-practices", "organizational-transformation", "walkthru"]
+++

APPENDIX IV

Kanban Scenarios and FAQs
 
1. I just had a Task assigned to me with the required Notes and a Priority, but I am unsure of the goal or Outcome (the Work Product) intended.  Before I begin work on the Task, I need a couple of clarifications.  What do I do?
 
A: Contact your Manager or the Task Stakeholder: usually the Service Desk or the PM, but can anyone on the Team who logged the request.  Usually Task Notes contain the intended Work Product (or Outcome) needed, so if this is missing then proper Backlog Triage was not performed.  The Kanban Board Admin can also be helpful here.
 
2. I am going on PTO or Vacation and I have unfinished Tasks.  What do I do?
 
A: You move your Active Tasks from the IN PROGRESS Lane into the ICE BOX Lane for Parking (Task is paused) and notify your Manager or Kanban Board Admin of any Tasks that are rated High or Urgent Priority.  Depending on how long you are out, Tasks with High or Urgent Priorities may be re-Assigned.  Only Medium or Low Priority Tasks will generally "wait" and remain paused, until your PTO ends, subject to various conditions including Task Stakeholder communication.
 
3. I received direct email from the Service Desk containing an Escalation regarding a User Problem and a Request to look into it.  No one on the Team has ever seen, or fully understands, this problem.  So it requires a bit of time and RCA and testing rounds on my IT VM.  The Task has a Default Priority with no Due Date.  I have no Active Tasks and will begin my work immediately.  What else do I need to do?
 
A: After you took ownership of the  a Task from the Service Desk Escalation, you just need to respond to the Service Desk email that you are starting RCA.  If the Task does not have an ITSM Ticket Number, be sure and get that info at some point and place it into the Task Notes.  Any Escalation from the Service Desk that is not an unplanned Downtime Event should normally reference an ITSM Ticket on the Task. 
 
Note to any one who self-creates a Task into the BACKLOG, to Pull and work immediately yourself: whether it is an Escalation or not, if you will not wait for the Kanban Board Admin to review your Task -- you must verify the Task has "The Three Things" required for that Task to be in the Active Kanban Lanes.  Failure to do this might result in the Board Admin grabbing and Reverting your own Task (remove from Work In Progress / return it to the BACKLOG) and contact you! 
 
Create Complete Tasks that have all requisite items to be Actionable ("The Three Things").  Don’t be that guy who is trying to enter your own Tasks willy-nilly, without complete info on the Task: you will get called-out for this in BMMs and DSUs!
 
4. Shouldn’t a Task just Pushed to me by someone other than our Kanban Board Admin else stay in the BACKLOG Lane for review?
 
A: No. Tasks, when first-entered into the BACKLOG Lane, can be Assigned to you right away if the Task has a clear Outcome or Purpose, a Priority or Due Date, and your WIP count is under 3 Tasks on the IN PROGRESS Lane.  Tasks that have "The Three Things" and fall under the SysOps mission (falls in our role, or brings Value to the IT Department Team) can move to the IN PROGRESS Lane right away without a BMM having to occur.  If it has those 3 things it may be immediately Front-Lined (prioritized) and queued for Assignment by the Kanban Board Admin in coordination with an IT Manager or the PM. 
 
Remember: The BACKLOG Lane is not a "place for work to wait" - if a Task lands in the BACKLOG with our required items set on that Task, the Task may be Assigned to a Task Owner or Task Resource to work on it just as soon as a Resource is available or the requested SME can work on it.  While regular BMMs happen, properly-defined Tasks in the BACKLOG Lane do not wait for meetings if the Task arrives clarified, prioritized, and doesn’t require Value Management.  Such Tasks can be immediately Pulled by, or Pushed to, a Task Resource.
 
5. I thought Stand-Ups are when and where we decide what to work on from the BACKLOG.
 
A: No. Daily Stand-Ups are concerned primarily with discussing non-BACKLOG Tasks that are already Active, Parked, or Blocked.  We review Tasks that are progressing on the board and we compare their Priorities and Due Dates, to ensure that Tasks of higher Priority and shorter terms are getting addressed. 
 
Deciding "what to work on" on involves BACKLOG Triage and that happens elsewhere in Backlog Maintenance Meeting (BMM).  We do not decide "what to work on"  in DSUs.    
 
If a Team member is present who has no Assigned Tasks on the Active Kanban Lanes, the Project Manager (if present at the Daily Stand-Up) or Kanban Board Admin may offer a Task from the BACKLOG Lane to that Team member at the end of the DSU; otherwise Team members with no Tasks can be given un-started Tasks by other Task Owners present at the DSU.  Failing that, Team members without Tasks can co-work Tasks until the next BACKLOG Triage is performed, and more Tasks are Assigned. 
 
In the Daily Stand-up we identify the highest priority Blocked Tasks and IN PROGRESS Tasks and discuss those Tasks so that the PM or a Kanban Board Admin might help remove any hurdles.  And lastly we discuss Tasks in the ICE BOX and TESTING QA Lanes for prioritizing based on those Tasks' Priority or Due Date.
 
So Stand-Ups are about Active ongoing Tasks on the Kanban Board, who has Blocked Tasks, and getting any Paused Tasks out of the ICE BOX and BLOCKED Lanes.  We may, from time to time, of course discuss Tasks in the BACKLOG Lane; however, Tasks in the BACKLOG Lane do not wait for Stand-Ups or meetings to get a Task prioritized and Assigned to a Task Resource or Task Owner.  
 
6. Why is attendance to Daily Stand-Up not required?  Shouldn’t it be mandatory?
 
A:  We are all professionals committed to doing our best work, and so we keep DSUs flexible and functional even if the same Team members cannot always attend.  Also: every single one of us are each too busy to be micro-managing DSU attendance, when we already understand that DSUs are critical to Task Progression!  You either make the meeting, or you don’t.  The DSU happens either way, and you can catch up later.  See this deeper explanation, for more info about why DSU attendance is not mandatory.
 
7. I have a Task I am stuck on and need help, and so it feels like it is "Blocked"by me being stuck…and not making progress.   If I cannot get un-stuck, would I move my Task to the Blocked Lane when asking for help?
 
A:  Generally speaking, you probably should move it to the Blocked Lane before the next DSU.  Unless you get additional help from a Team member to help you remove the Block, your decision to move it to the Blocked Lane is correct.
 
If you own a Task that you cannot finish for any reason, regardless of Priority or Due Date, your Task is considered Blocked.  So it is your responsibility to indicate this (by using the Blocked Lane and asking for help before or during the next DSU).  
 
The goal of our Kanban Board is Task progression.  So when you are stuck and unable to move forward with a Task, it is on you to say-so in DSUs or by contacting a Team member for help.
 
There is no penalty or Review Criteria, for people who get stuck or Blocked on Tasks.  But there IS a penalty if you hold onto a Blocked Task for too long without asking for help!  Don’t be that guy!
 
We should challenge ourselves and seek opportunity to grow and skill-up, but if we Pull (or get Assigned) a Task that was "biting off more than you can chew" and your are stuck: then you are Blocked for the time-being.  Remember the Team is here to help you get un-stuck and un-Blocked: so use the DSU as a forum to ask for help,  Use the Team DSU, help us… help you!
 
Our Team embraces a culture of collaboration and encourages all Team members to ask for help when needed, there is no shame in asking for help at ANY time -- and you may even avoid moving your Task into the Blocked Lane!  We absolutely discourage not asking for help when stuck, because it creates an intolerable Risk for the Team for Orphan Tasks.
 
A good rule-of-thumb is: if you cannot get un-stuck on your Task within a day or two on a Task that is Medium or Lower Priority, move it to the Blocked Lane and prepare to discuss the Task at the next DSU.  If the Task Priority is High or Urgent, don't wait for the next-day's DSU to ask for help: move it to the Blocked Lane and let the Team know the high-priority or urgent Task is Blocked.  Blocked Urgent Tasks may be nominated for a Swarm under certain conditions.
 
8. I am Blocked on a Medium or Low Priority Task, and it is something I don’t understand or know how to get past.  I would like to request a Swarm for help in the next DSU. How do I go about doing that?
A: You don’t.  You cannot request a Swarm on a Medium or Low Priority Task, regardless of Due Date: Swarms are reserved for Urgent prioritized Tasks that would have received that Priority in Backlog Triage or later through Front-Lining (changing Task Priority).
 
If your Task has a Due Date coming up, but the Task is not High or Urgent priority, then you should reach out to any free Team member to help out.  Otherwise if you feel a Swarm is needed, get your Task Front-Lined (priority changed) by the Kanban Board Admin before you Nominate it for a Swarm at the next DSU.
 
If your Task has no Due Date and has Default (Medium) Priority or Low Priority, you should instead seek out an SME from the Team to help you out in a one-on-one or group meetup.  But not a Swarm: a Swarm is every available Team member (we drop everything, usually) and so Swarms are a use of Task Resources that are reserved for more urgent Tasks.  If your Task Urgent, by all means you may nominate it for Swarm at the next DSU.
 
9. I have an idea for a Task with a set of Sub-Tasks, that could result in a huge improvement in Systems Operations, or could benefit the IT Department as a whole.  Do I enter a draft for this Task into our BACKLOG for discussion at the next BMM?
 
A: No, your Task ideas should go into the Idea Pipeline.  The Idea Pipeline is a "pre-Backlog" hidden Lane (or Bucket) where we capture initial ideas or requests for further analysis or evaluation, before they become Tasks added to the BACKLOG Lane.  These are not Task Requests by our traditional Task Stakeholders (Service Desk Escalation, our PM, etc) but are instead where we place our ideas for Tasks.  These ideas or requests get reviewed during Backlog Maintenance Meetings (BMM), where they may be refined into Tasks for our BACKLOG, thus moving into the BACKLOG Lane for the next BMM.  Actionable Task ideas or user stories will always get a full hearing during BMMs.
 
10. I understand any of us can place Task Requests into the BACKLOG, at any time, for review by the Kanban Board Admin or BMM  Meetup Team. 
 
Is there any scenario where I can just enter my own Task when someone asked me for something, and just proceed to work on that Task?  Can I do this and bypass Backlog Review?  Just move my Task directly into the IN PROGRESS Lane myself?  My WIP Count is less than 3.  Or do I have to wait, after I enter the Task Request into the BACKLOG?
 
A: Generally for most non-Urgent Task Requests, when you are self-entering a Task yourself -- it usually best to Push (Assign) that Task to yourself and then wait for the Kanban Board Admin to review it.   This will be a brief wait: chances are it is reviewed within an hour or less, and does not have to wait for the next BMM.  You can call the Board Admin, get your "+1" and move on.  For Pushed or Pulled Tasks, our process requires that only reviewed Task Requests transform into Active Tasks and Works-In-Progress - but there are always exceptions. 
 
Just use your best judgement, because it will be seen if you self-create / work Tasks when other older Task(s) of higher-priority might already exist in the BACKLOG!
 
Exception to the above: your incoming Task Request is an Escalation Task relating to an unplanned Downtime Event.   Obviously in that case it is full steam-ahead: Enter the Task, get "The Three Things" established and place the Task on the EMEREGENCY Lane to work it.   Otherwise, if the Task Request you are self-entering is not an emergency, you should probably wait and get the Kanban Board Admin to briefly review and "+1" co-sign your self-created Task.
 
Don’t be that guy who is always entering your own Tasks willy-nilly, without proper info on the Task: you will get called-out for this in BMMs and DSUs!
 
11. This week most of my work has been Escalations from the Service Desk that are quick and easy break/fix Tickets.  Most of them I have resolved in less than a day, sometimes less than 2 hours.  Do I need to bother creating a BACKLOG Task entry for these?  Or when should I create Escalation Tasks?
 
A: No!  You absolutely you should not create Escalation Task entries for short-duration break/fix Tickets of any Priority from the Service Desk.  Those Tickets can just be worked and closed right there in our ITSM System!  No need to manage this kind of work in Kanban, which is there to manager longer-firm work Tasks that will live longer than 24 hours.
 
Service Desk Escalations Tasks only need to be created for Escalations that will be long-lived require lengthy RCA or SME technical work, or for issues that have not ever been encountered and may require further effort by the SysOps Team (Swarm, etc).  See the Escalation Task term for more information and guidance here on when / when not to create an Escalation Task.
