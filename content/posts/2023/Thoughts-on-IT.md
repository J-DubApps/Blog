+++
date = '2023-12-22T20:10:26-06:00'
draft = false
title = 'Thoughts On IT: 2023 Edition'
type = 'post'
tags = ["tech", "devops", "best-practice", "enterprise-it", "opinion", "project-mgmt", "thought", "funny", "best-of", "career"]
+++

  <style type="text/css">
        .e-mail:before {
            content: attr(data-website) "\0040" attr(data-user);
            unicode-bidi: bidi-override;
            direction: rtl;
        }
    </style>

<div style="font-size: 13px;">
This year, something a little different.  No opinion-piece on the blog, just 50 notes of hard-earned wisdom.  Garnered from funny or painful experiences spanning two decades in InfoTech. Enjoy. 
</div>

1. It's always DNS.
2. RTFM.
3. Always ask: which tech solution, or method, requires the Least Amount Of Administrative Effort. You can accomplish a *whole lot more*, when you have *less to do*.
4. **Read-only Friday** — *Never* deploy to prod or make changes on Fridays.
5. If it can go wrong, it *will* go wrong.
6. If given enough time, most tickets solve themselves.
7. When in doubt, blame the security configs or your predecessor.
8. Backups don't really exist unless you have multiple copies (3-2-1 rule). Backups always work, restores not so often.  Just because the backup said "success" doesn’t mean it backed anything up. Trust, but verify. A backup is not a backup unless you have *recently* performed a restore from it, better yet do automated restore tests with reports frequently. Always test your backups - otherwise you like playing Russian roulette with 5 bullets in the gun.
9. Backups *will* fail, see rule # 8.
10. RAID is *not* backup.
11. ***Document all the things***. If your documentation takes longer to read than to fix the problem, you're doing it wrong.
12. Automate everything you possibly can (...that you've had to do > 2 times).
13. Don't make yourself a single point of failure.
14. Don't let other people make you a single point of failure.
15. Always check the logs.
16. Google is your friend. So is ChatGPT.
17. Test, but verify.  It's not just for backups.
18. Never stop learning.
19. A lot of end user issues are the direct result of IT focusing on technical solutions and ignoring user experience.
20. A lot of user experience issues are the direct result of the C-Suite not being invovled in setting IT Priorities & Policies.
21. IT departments need to remember we’re there to solve business problems: if your solution is amazing technically, but doesn't serve the business, you didn't do you job.
22. Know where the food is located.
23. Never *EVER* let Perfect be the enemy of *Good*, or prevent forward-progress.
24. The Infrastructure is *not* your baby https://github.com/dbeta/RulesofIT/blob/main/Rules/19.md
25. If you make something idiot proof, the world will make a better idiot.
26. Nothing is user-proof, either.
27. There’s no crying in IT. Hyperventilating and panic, yes...but definitely *no* crying.
28. If it’s not in the ticket, it didn’t happen.
29. When it comes to network engineering, coding, or systems management: Design is *everything*.
30. Technology does *not* fix bad design.
31. If you are the smartest person in the room, you are in the ***wrong room***.
32. Always mispronounce with authority.
33. Temporary is *permanent*: “*this bandaid fix on the server is just temporary...*” —somebody 5 years ago.
34. There are no policies, only *levels of resistance*.
35. The end user *will* ***lie***.
36. Don't acknowledge or provide technical info about an active outage event to users: deflect until the problem is fixed. Nobody gets explanations until *after* your team analyzes the root cause, *after* uptime is restored. That's what post incident-reports are for.  Don't allow VIPs to bait you into an explanation death-spiral *while* still troubleshooting: they don't care and are only interested in blame-assignment. Reason and patience only return after services get restored.
37. Don't do special favors because people will expect it everytime.
38. Redundancy is key: two is *one*, one is ***none***.  Redundancy is key: two is *one*, one is ***none***.
39. Get that request in writing.
40. When estimating time, add at least 50%.
41. Good, Cheap, Fast. *Pick 1*.
42. Don't chain people on emails where they have to read a week-long thread, to even understand the conversation or context.
43. Design for uptime and redundancy where you can: if I can’t randomly unplug something in your datacenter, without a production outage, it’s a disaster waiting to happen.
44. <b>https://xyproblem.info/</b>
45. <b>https://nohello.net/en/</b>
46. Remember that we work in a service industry.
47. ⁠Always keep your <a href="https://julianwest.me/Resume/">resume updated.</a>
48. Work life balance - Set standards with how approachable you are outside of work hours.
49. Dev is *dev* and prod is *prod*. NEVER put anything that impacts prod in your dev environment. 
50. AI won't take your job, it's someone using AI that will take your job. <br /> <br />

***Bonus***. If you're in charge, and you have to tell people you're in charge...you're *not* in charge.