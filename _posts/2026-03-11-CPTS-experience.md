---
title: "My Hack The Box CPTS Experience"
description: "My experience completing the Hack The Box Certified Penetration Testing Specialist (CPTS) certification, including coursework, labs, exam strategy, and reporting tips."
date: 2026-03-11 00:00:00 +0800
categories: [Certifications, CPTS]
tags: [hackthebox, cpts, penetration-testing, cybersecurity, red-team]
---

# My Hack The Box CPTS Experience

On 13 January 2026, I officially passed the Hack The Box Certified Penetration Testing Specialist (CPTS) exam.

During the process I learned a number of lessons, picked up advice from others online, and refined my own methodology for penetration testing. I decided to write this post to document the journey and share some practical tips for anyone planning to take the certification.

Before starting the Penetration Tester Job Role Path, I already had some exposure to penetration testing in my professional career as a junior penetration tester. However, most of my experience had been focused on GRC (Governance, Risk, and Compliance).

Fortunately, the CPTS course is designed to start from the fundamentals, so even those without significant pentesting experience should still be able to follow along.

This post covers:

- Coursework experience  
- Lab preparation  
- Exam experience  
- Reporting phase  
- Final thoughts and advice  

---

## CPTS Coursework Experience

The Hack The Box CPTS path contains 28 modules, covering topics ranging from penetration testing fundamentals to performing a complete external and internal penetration test.

I started the course in February 2025 and completed the coursework (excluding the *Attacking Enterprise Networks* module) by August 2025.

On average I spent roughly:

- 2 hours per day
- approximately 365 hours total

This wasn’t completely consistent, as I took several week-long breaks during the process.

Overall, I found the time estimates provided by Hack The Box to be fairly accurate. If someone had 8 hours per day available, it would likely be possible to complete the path within the recommended 42 days.

The modules themselves are very well structured and written in a way that is easy to understand while avoiding unnecessary jargon.

Additionally, I would reccomend everyone to use their own lab environment instead of relying entirely on Pwnbox.

This will allow you to customize the environemtn to align with your workflow. Additionally and custom scripts, wordlists and tooling configurations you need can be easily accessible. Over time, this becomes significantly more efficient than starting fresh each session.


### Note Taking Strategy

Throughout the course I maintained detailed notes that included:

- commands
- tool usage
- enumeration techniques
- exploitation examples
- when to use each technique

Over time these notes evolved into a personal pentesting field guide, which proved extremely useful during the exam. This did not include detailed explanations of how services worked, just the techniques to test them.

### When You Get Stuck

There where a few cases where i got stuck in the assessments in the coursework. These are great opportunities to work on your problem solving skills, use this time to review your notes and make sure it aligns to the course material. 

If you're still stuck after a few hours, look up the module you're stuck on, on the HTB forums, and try to avoid as many spoilers as possible.

---

## CPTS Lab Preparation

At this stage it was August and the best time for me to take the 10 day exam was in december, this left my with 3 months to prepare for the exam. After a short hiatus, I planned to complete 57 practice machines to prepare.

These were selected using:

- **[TJ Null's CPTS Preparation List](https://docs.google.com/spreadsheets/u/1/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/pubhtml)**

- **[IppSec's Unofficial CPTS Preparation Playlist](https://www.youtube.com/watch?v=H9FcE_FMZio&list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5)**

My target lab roadmap looked like this:

![Planned Hack The Box labs for CPTS preparation]({{ site.url }}/assets/img/image-3.png)

After approximately 130.75 hours, I completed 48 out of the 57 planned labs.

This also included completing the Attacking Enterprise Networks (AEN) module *blind*, using only the techniques learned throughout the coursework.

During this process, I took detailed notes in all labs so i can use them as a reference in the future, I updated my notes where needed, and updated any scripts or wordlists along the way.

### Pivoting with Ligolo-ng

During this stage I also expanded my notes to include pivoting using Ligolo-ng.

I strongly recommend using Ligolo-ng rather than tools like Chisel or Meterpreter, it is far more efficient once configured properly and simplifies pivoting significantly.

A helpful guide can be found here:
- **[arth0s's ligolo-ng pivoting reverse shells and file transfers blog](https://www.youtube.com/watch?v=H9FcE_FMZio&list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5)**

---

## CPTS Exam Experience

By this point I felt confident enough to schedule the exam. With my notes prepared, I clicked Start Exam.

The environment was fairly straightforward, the setup is very similar to the Attacking Enterprise Networks module, where you are given a scope of work and a target to start testing.

### The First Flag

The first flag took almost an entire day to obtain.

Eventually, I returned to my notes and restarted my enumeration process using updated wordlists, which led me in the right direction.

After that initial hurdle, the workflow felt very similar to the practice labs where I would continue to enumerate, find a vulnerability, exploit it, and repeat.

### Documentation During the Exam

During the exam, I took detailed notes covering every command I ran and screenshots of successful outputs so that i could review what i have done if I got stuck.

The reporting module suggests using tmux for logging, which is extremely useful. Especially during live engangements where a client might as what command you ran at a specific time yesterday, logging will save you.

A good tmux guide can be found here:

- **[Haft's Tmux environment setup](https://www.youtube.com/watch?v=H9FcE_FMZio&list=PLidcsTyj9JXItWpbRtTg6aDEj10_F17x5)**

### Tracking Findings During the Exam

Once I had a finding (not just a flag but any security finding), I would write a rough draft in my notes right away using the given format, this would later be cleaned up in the reporting phase:
- Title
- CWE (added during reporting)
- CVSS (added during reporting)
- Description
- Impact
- Remediation
- References (added during reporting)
- Reproduction Steps (Include commands and screenshots)

Without this, i would have spent at least another day just going back through the lab taking screenshots and confirming my findings. 

### Getting Stuck Again

There were a few points during the exam where I became stuck, particularly around Flag 9, taking frequent breaks, reviewing my notes helped and researching techniques helps. 10 days is a lot of time to get this exam done, so stay level-headed and prioritise sleep.

It ultimately took 6 days to obtain the 12 required flags needed to pass.

### CPTS Reporting Phase

The report writing phase took around 3 days.

I decided not to use SysReptor, as I didn’t yet have a good enough findings repository prepared.

As I would have needed to rewrite all the findings anyway, I used the Word template provided by Hack The Box.

Since I already had the draft finings ready, I consolidated a few that were very similar and formaly wrote them up utilising extneral rousources along the way. Helpful reference sources included:

- **[MITRE CWE](https://cwe.mitre.org/)** – Common Weakness Enumeration database
- **[MITRE ATT&CK](https://attack.mitre.org/)** – adversary tactics and techniques framework
- **[MITRE CAPEC](https://capec.mitre.org/)** – attack pattern classification
- **[OWASP](https://owasp.org/)** – web application security resources and standards
- **[Hacking Articles](https://www.hackingarticles.in/)** – penetration testing techniques and walkthroughs
- **[GTFOBins](https://gtfobins.org/)** – Unix binaries useful for privilege escalation
- **[NIST NVD](https://nvd.nist.gov/)** – National Vulnerability Database
- **[Exploit Database](https://www.exploit-db.com/)** – public exploits and vulnerability references

Following the methodology described in the CPTS reporting module, my final report reached 116 pages.

Most of this consisted of the detailed compromise walkthrough, findings, and screenshots.

### CPTS Exam Result

On 22 December 2025, I finally submitted my report and began the wait.

After 19 days, I received confirmation that I had passed the CPTS certification!

![Hack The Box CPTS exam passed status]({{ site.url }}/assets/img/image-4.png)

Some key advice for anyone planning to take the CPTS would be to no rush the process.

The skills you build while completing the course are far more valuable than the certification itself.

Good luck to anyone currently working towards CPTS.