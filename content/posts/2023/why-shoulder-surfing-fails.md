+++
date = '2023-04-07T20:10:26-06:00'
draft = false
title = "Downtime-Hovering On The Lead Troubleshooting Engineer"
description = 'Why Shoulder Surfing Your SME Is Counterproductive'
type = 'post'
tags = ["tech", "devops", "best-practice", "enterprise-it", "opinion", "thought", "beginner-fundamentals", "leadership", "self-development", "troubleshooting"]
+++
**When systems are *on the fritz* and everyone is scrambling to restore service**, it’s tempting to just hover behind the most experienced colleague—usually your Lead Engineer or nearby [Subject Matter Expert](https://en.wikipedia.org/wiki/Subject-matter_expert) (SME)—and observe them in action. The logic seems sound: “Watch what the expert does, maybe jot down notes, and learn advanced troubleshooting techniques on-the-fly.” ***In reality*** the classic “shoulder surfing” approach consistently *falls flat* and can even *hinder the diagnostics* and troubleshooting. Below I am going explain ***why this is***—and **why it’s not always the best way to get cross-training** or close [skills gaps](https://julianwest.me/Blog/skill-gap/). <br />

## Stressful Environment and Split Priorities

When a critical system is down, pressure is at its highest. The Lead Engineer (or SME) working the problem is focused on: <br />
•	**Identifying the root cause** of the issue <br />
•	**Implementing the fastest route to resolution** <br />
•	**Communicating with stakeholders** (if necessary, and it often is necessary...) <br />

Add a small crowd of curious onlookers, and you shift the SME’s focus. Now they’re juggling “teaching mode” with “fix-it mode.” This is a recipe for mistakes and oversights because the SME is split between effectively explaining their steps and responding to unexpected system behaviors.

## “Training Under Fire” Almost *Never* Works

In a perfect world, we’d capture each fix step-by-step, break it down, and lead a discussion to ensure deep understanding. But during an outage, no one has the luxury of time to thoroughly explain what’s being done and why. <br />
•	**Complex steps** often rely on advanced knowledge, partial scripts, or specialized tools that aren’t intuitive to someone unfamiliar with them. <br />
•	**Reasoning paths** in real-time troubleshooting can be disjointed, contradictory, or adapted on the fly as new information emerges. <br />

Trying to transform a live outage into an on-the-spot training session forces the SME to dilute their focus, risking both the fix process and the educational goal.

## Rapid-Fire Troubleshooting Doesn’t Translate (...*to understanding*...)

Experts work based on a mental library of known issues, logs, or system behaviors. They might test quick hunches or recall something from a past incident. Observers may only see a blur of command lines, console messages, or configuration checks. Without context, it’s hard to link these steps to underlying principles. <br />
•	**Not all steps are linear**: Sometimes the SME jumps between tasks—checking a log one second, adjusting a firewall rule the next. <br />
•	**Context can be lost**: Observers might see changes being made without understanding the root cause or how multiple system components fit together. <br />

## The Distraction Factor

There’s a real performance penalty when someone feels closely monitored. You may notice your SME pausing to explain themselves, triple-checking trivial things out of self-consciousness, or simply losing their train of thought mid-troubleshoot because they’re explaining each keystroke. <br />
•	***Reduced flow state***: The expert can’t enter “full concentration mode” ([Flow State](https://en.wikipedia.org/wiki/Flow_(psychology))) if they’re worried about *how well* they’re *teaching you*. <br />
•	**Increased error likelihood**: Any additional mental load—*like an a*udience*—adds a layer of stress that can translate to mistakes or second-guessing. <br />

## Note-Taking Doesn’t Always "Stick"

Observers often try to take notes: copying down commands, writing bullet points of steps. But this approach doesn’t usually hold up in a high-speed troubleshooting scenario. And any nearby SME seeing you take notes is usualy an identifier of a [*Skills Gap*](https://julianwest.me/Blog/skill-gap/) that you have going on.  Here are 3 reasons why note-taking is counterproductive ***during*** *a downtime event*: <br />
•	**Out-of-context commands**: Capturing commands without deeper context leads to confusion when you try them later. <br />
•	**Rapid changes**: You might not have enough time to note why a particular file path is important, or when a certain configuration flag should (or shouldn’t) be used. <br />
•	**Messy or incomplete**: Because you’re focused on capturing details quickly, your notes might be incomplete or indecipherable afterward.

## Better Alternatives for Effective Learning

1.	**Scheduled Debriefs and Walkthroughs** <br />
After the outage is resolved, schedule a debrief or “post-mortem” session. Have the SME calmly walk through *what* went wrong, *why* it went wrong, and how they identified and fixed it. This environment—without the chaos of an *active downtime incident*—encourages methodical explanation, Q&A, and deeper understanding. <br />
2.	**Documentation and Knowledge Bases** <br />
Encourage your SME to document known fixes, tips, and best practices when not under pressure. A well-curated internal knowledge base is more valuable than sporadic notes taken during a crisis. [Visit this link](https://julianwest.me/Blog/documentation-manifesto/) for my recommended Documentation practices <br />
3.	**Hands-On Training Sessions** <br />
Provide structured labs or sandbox environments to try out the SME’s troubleshooting steps in a controlled setting. Working through a simulated problem fosters better retention and confidence. <br />
4.	**Mentorship or Pairing** <br />
Instead of lurking in the background during an outage, partner with your expert outside of crisis situations. Shadow them on routine checks and less critical tasks, where they can afford the time to explain processes and reasoning without the pressure of a ticking clock. <br />
5.	**Formal Cross-Training Programs** <br />
Encourage SMEs to create training modules or hold lunch-and-learns. This approach helps shift from a reactive “learn when it breaks” approach to a proactive continuous-learning culture.

# Wrapping-Up

While it might be tempting to learn from your best in-house expert by simply watching them in action during a crisis, “*shoulder surfing*” usually fails to provide meaningful cross-training or advanced troubleshooting *know-how*. The stress of the moment, the complexity of the tasks, and the need to focus on rapid recovery all make for a ***poor learning environment***—both for the *SME* ***and*** *the observer*. <br />

A better approach: **wait until the dust settles**. Conduct a proper review once systems are stable, and invest in **structured**, **calm**, and ***intentional*** training sessions with Senior and Jr Engineers. **In the long run, that’s how you’ll really glean insights from your team’s subject matter experts and build a more resilient IT organization.**

# *I am rooting for you*!

***Related Posts***:  <br />

[My Approach To Cross-Training](https://julianwest.me/Blog/empowering-independence-it/). <br />
[My recommended best-practices on documentation](https://julianwest.me/Blog/documentation-manifesto/). <br /> <br />

 <img src="https://julianwest.me/Blog/posts/images/shoulder-surfing.jpg" alt="Alt text">