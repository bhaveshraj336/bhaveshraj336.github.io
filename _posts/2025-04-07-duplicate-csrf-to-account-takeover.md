---
layout: post
title: "Duplicate CSRF Leads to Account Takeover"
date: 2025-04-07
author: Bhavesh aka Shellbreaker
---

## Introduction

Hey everyone, Bhavesh aka **Shellbreaker** here! Cybersecurity is my passion—both in my role as a security engineer and during late-night bug bounty sessions. Join me as I uncover vulnerabilities and explore the wild world of cybersecurity, one loophole at a time.

## What is CSRF?

**Cross-Site Request Forgery (CSRF)** is an attack that forces authenticated users to perform unwanted actions on a web application where they're currently logged in. It abuses the trust that an application has in a user's browser.

## The Chase Begins

This story started with a site featuring two dashboards—one for uploading images and another for managing user settings. Clicking the settings link opened a new page that included a curious URL clue about the previous page...

## Unexpected Turns

Naturally curious, I tested some JavaScript injections—nothing worked. After a break, lightning struck! I tried a different payload and suddenly... **a pop-up appeared**. It was a **Self-XSS** vulnerability.

## From Self-XSS to Account Takeover

Though self-XSS is often considered low-severity, I saw potential. I hit up my buddy **Brute Logic**, and together we brewed a daring plan: **account takeover**.

Why? The site allowed changing email addresses **without password confirmation**. I crafted a malicious payload that triggered the self-XSS and changed the victim's email address—effectively hijacking their account.

## Duplication Drama and Victory

Excited, I submitted the report—only for it to be marked a **duplicate** and labeled as **just CSRF**. Bummer.

But I didn’t back down. Brute Logic reminded me that **XSS can bypass CSRF protections**. Armed with that, I clarified the situation to the triage team—and boom, the report was upgraded to a **P2 severity**.

### 💰 A rewarding bounty followed.

## Lessons Learned

- **Persistence pays off.**
- **Collaboration matters.**
- **Linking vulnerabilities leads to big wins.**

## Join the Adventure

I’m all about knowledge sharing and helping others level up. Follow my journey as I dive into this ever-evolving field. Remember: even small bugs can lead to big break-ins.

---

If you enjoyed this post and want to support my work, consider buying me a coffee ☕️  
**[👉 Buy Me a Coffee](https://buymeacoffee.com/shellbreaker)**

Follow me as **Shellbreaker** on HackerOne, Bugcrowd, and Intigriti!
