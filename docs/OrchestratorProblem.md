# Orchestrator Definition
Ralph sent an email with [Orchestrator Definition](https://docs.google.com/document/d/1QZtYFcDpkfOKJbFhkw-XPuD1eix0ovXSOe3cyEQivQQ/edit) attached.  Note the link is the actual attached google doc.  These are my response notes.

The question being asked was:
How does RansomShield define “network” to select which devices should be self-healed?

The questions before seemed to seek:
What is the User interface mechanisim Hacker Strike should implement to regulate RansonShield App Process Blocker within an associated user group.

Notes:
I do like the new diagram, and if you notice the labels... it is very 'Ralph'.  The diagram does not show up in the above link, but the pdf attached to the email:

![hs-arch](./images/hs-arch.png)


1. Dashboards and Management
2. RansomShield App
3. HackerStrike App
4. Process Blocker or all three parts of #2 RansomShield App
   1. Process Monitor
   2. Micro Neural Network
   3. Process Blocker
5. Cloud Console

It looks as if the numbering is some sort of workflow for Ralph's head... just a guess.  As for me, I sorted this out in my head [See docs/README.md](./README.md) :

1. hs-client - used to collect telemetry and execute behavior mitagation
2. hs-telemetry - api based web service target used by client for telemetry collection
3. hs-mllab - lab for machine learning pipline used for the creation of client mitagation neural patterns
4. hs-malwarelab - lab used to create malware use telemetry for hs-mllab
5. hs-dsllab - lab used to model Domain Specific Language useage patterns to obtain deeper business specific use patterns
6. hs-customer-webportal - gui portal for ralph-types to show client value
7. hs-automation-webportal - gui portal for ralph-types... IMHO this should just be a deployment CI/CD pipeline

So, as I look at this, I think the answer is:
Use your Baseline Behavior Injector.
