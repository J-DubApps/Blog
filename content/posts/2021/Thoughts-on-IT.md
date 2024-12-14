+++
date = '2021-08-02T20:10:26-06:00'
draft = false
title = 'Thoughts On IT: 2021 Edition'
type = 'post'
tags = ["tech", "devops", "best-practice", "enterprise-it", "opinion", "project-mgmt", "thought"]
+++

1. It's always DNS.
2. RTFM.
3. Always ask: which method will require the Least Amount Of Administrative Effort: you can accomplish a whole lot more, when you have less to do.
4. Read only Friday — Never deploy to prod or make changes on Fridays.
5. If it can go wrong, it *will* go wrong.
6. If given enough time, most tickets solve themselves.
7. When in doubt, blame the security team or your predecessor.
8. Backups don't really exist unless you have multiple copies (3-2-1 rule). Backups always work, restores not so often.  Just because the backup said "success" doesn’t mean it backed anything up. Trust, but verify. A backup is not a backup unless you have *recently* performed a restore from it, better yet do automated restore tests with reports frequently. Always test your backups - otherwise you’re a Russian roulette player with 5 bullets in the gun.
9. Backups *will* fail, see rule # 8.
10. RAID is not backup
11. Document all the thingsIf your documentation takes longer to read than to fix the problem, you're doing it wrong.
12. Automate everything you possibly can (...that you've had to do more than two times).
13. Don't make yourself a single point of failure
14. Don't let other people become a single point of failure
15. Always check the logs
16. Google is your friend
17. Test, but verify
18. Never stop learning
19. A lot of end user issues are the direct result of IT focusing on technical solutions and ignoring user experience.
20. A lot of user experience issues are the direct result of the C-Suite not writing company IT policies.
21. IT departments need to remember we’re there to solve business problems: if your solution is amazing technically, but terrible business, you did a terrible job. 
22. Know where the food is located
23. Don't let perfect be the enemy of good.
24. The infrastructure is not your baby https://github.com/dbeta/RulesofIT/blob/main/Rules/19.md
25. Nothing is user-proof. If you make something idiot proof, the world will make a better idiot.
26. There’s no crying in IT.
27.  If it’s not in the ticket, it didn’t happen.
28. When it comes to networking, coding, or systems management: Design is everything. 
29. Technology does not fix bad design 
30. If you are the smartest person in the room, you are in the wrong room.
31. Always mispronounce with authority.
32. Temporary is permanent (“this bandaid fix on the server is just temporary…” —somebody 5 years ago)
33. There are no policies, only levels of resistance.
34. The end user will lie.
35. Don't acknowledge or confirm a fault (or technical specifics of an issue) to users:  instead deflect until the problem is fixed
36. Don't do favors because people will expect it everytime
37. The ISP and/or Vendor will lie.
38. Get that request in writing.
39. When estimating time, add at least 50%.
40. Good, Cheap, Fast. Pick 1.
41. Don't chain people on emails where they have to read over weeks of messages, to understand the conversation.
42. Design for uptime and redundancy where you can: if I can’t randomly unplug servers in the datacenter without production outages, it’s a disaster waiting to happen.
43. https://xyproblem.info/
44. https://nohello.net/en/
45. Remember that we work in a service industry.
46. ⁠Always keep your <a href="">resume updated.</a>
47. Work life balance - Set standards with how approachable you are outside of work hours.
48. Dev is *dev* and prod is *prod*. NEVER put anything that impacts prod in the dev environment. Dev-prod hybrid always creep into importance *right* as somebody resets the test-dev sandbox.
49. Don't confuse being responsible for an outcome as "being in charge".  Non-managers need allies to suceed, not underlings.
50. If you're in charge, and you have to tell people you're in charge...you're *not* in charge.