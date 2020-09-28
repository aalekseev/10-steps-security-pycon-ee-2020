<!-- sectionTitle: Misconceptions -->
import unicorn from '../assets/unicorn.png'

## What is Security?

SECURITY DOES NOT EXIST

<img className="content-center slide-bottom" src={unicorn} />

<p><small>
Image from <a href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2007266">Pixabay</a>
</small></p>

<!-- note

Right from the start let's be transparent about it - there is no such thing as security.
No system is 100% secure, and everything is mostly broken.

NEXT: With this out of the way, there are a few more topics that I would like to
clear out. In my opinion security problems so often related to people rather than code
that talking a more about security mindset is as important as stories about
cool vulnerabilities.
-->

---

## It is a job for _**only**_ security professionals

- **Staff, Sales, Marketing** - use strong passwords, know about phishing
- **Developers** - know about vulnerabilities and follow security practices
- **Engeneering Managers** - schedule secure audits
- **Project Managers** - work with client to avoid changes that will introduce security risks

<!-- note

Security is not just a thing for security experts do, and you don't need to know about.
An opposite, security is a shared responsibility. It is everyone job. And here is some examples:

- It is responsibility of the staff members, sales, marketing team, to use strong passwords and keep them in password manager, and also be aware about phishing attacks
- It is responsibility of the developer to look out for SQL injection, XSS attacks and more
- It is responsibility of the engeneering manager to make sure that secure audits are done regularly
- It is responsibility of the project manager to decline the changes from the client if it will be a security risk
-->

---

## Security is too complex to learn about

<!-- note

Well it is, especially cryptography, this stuff is tough.
But at the same time, it is fun and the stories about braking the system is most of the time
reads like a good detective story or a comedy where main character stores passwords on a sticky note 
on the workdesk.

But jokes aside, there are basic steps, if followed, that will make
your web application better protected than vast majority of sites. Amature hackers looking
for an easy target, and professional hacker will brake your site anyway
if you don't have a dedicated InfoSec team.
-->

---

##  My framework will protect me from all security threats

<!-- note

Yes, from some of them. Your framework will protect you on the start, but as application logic grows,
developers will itroduce more vulnerabilities in code and there will be less and less
help from the framework itself.

**NEXT**: So that was about misconceptions about security. And with that we can now look at the
things that we, as a developers, can do to make our applications more secure.
-->