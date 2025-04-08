---
title: "How '111111' Unlocked the Admin Panel — A Real Bug Hunting Story"
author: Bhavesh Rajpurohit
date: 2025-04-08
tags: [bug bounty, web security, real world bugs, penetration testing]
---

Have you ever tried something so simple during testing that it felt almost *too* silly to work?

Well, I did. And it unlocked the admin panel.

Let me explain.

## The Setup

I was testing the login flow of a web application. It used an OTP-based authentication system—nothing unusual. You enter your email or phone number, get a 6-digit OTP, enter it, and you're in.

While going through the flow, I thought:  
> "What if the developer left a hardcoded OTP for testing?"

So I tried the classic: `111111`.

No joke—**I got in.**

Straight to the admin dashboard. No rate-limiting, no alerts, no second factor. Just full access like I owned the place.

## Why This Happened

Digging deeper, I realized this was a leftover from development. Some developer had probably set `111111` as a universal test OTP. Maybe it made local testing easier. But somehow, **that logic made it to production**.

This isn’t uncommon. During development, shortcuts like:
- Hardcoded credentials
- Master OTPs or bypass codes
- Disabled security checks

...help speed things up. But the real risk kicks in when those shortcuts aren’t removed before go-live.

## The Impact

In this case, the OTP wasn't scoped to a test user. It worked **for anyone**, including privileged accounts.

This meant:
- Account takeover with zero friction
- Full admin access to the application
- Potential to modify, delete, or extract sensitive data

Had a malicious actor discovered this, it could've led to serious business and user impact.

## The Takeaway

What did I learn (and what should *you* take away)?

- **Always test the obvious.** Never assume something is “too dumb to work.” Try the simple things.
- **Developers need secure coding checklists.** Test credentials or backdoors should *never* reach production.
- **Code reviews and staging-to-production pipelines must include security checks.**
- **Security is everyone's responsibility**—not just the pentester’s.

## Final Thoughts

This bug reminded me that some of the most powerful vulnerabilities hide behind the *simplest inputs*. And honestly? That's what makes bug hunting fun. 🙂

Let me know—have you ever found something critical by trying something basic?

---

If you're into web app security and real bug stories, stick around. More stories coming soon.

Stay curious.  
— Bhavesh (aka shellbreaker)
