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
that talking about security mindset is as important as stories about
cool vulnerabilities.
-->

---

## It is a job for _**only**_ security professionals

- **Staff, Sales, Marketing** - use strong passwords, know about phishing
- **Developers** - know about vulnerabilities and follow security practices
- **Engeneering Managers** - schedule secure audits
- **Project Managers** - work with client to avoid changes that will introduce security risks

<!-- note

First misconception - It is a job for _**only**_ security professionals.

In reality, security is not just a thing that only security experts do.
An opposite, security is a shared responsibility. It is everyone job. And here is some examples:

- Staff, Sales, Marketing - use strong passwords, know about phishing
- Developers - know about vulnerabilities and follow security practices
- Engeneering Managers - schedule secure audits
- Project Managers - work with client to avoid changes that will introduce security risks
-->

---

## Security is too complex to learn about

<!-- note

Second misconception - Security is too complex to learn about

Well it is hard to learn about, especially cryptography, this stuff is tough.
But at the same time, it is fun and the stories about braking the system is most of the time
reads like a good detective story or a comedy where main character stores passwords on a sticky note 
on the workdesk.

But jokes aside, there are basic steps, if followed, that will make
your web application better protected than vast majority of sites.
Amature hackers looking for an easy target,
and professional hacker will brake your site anyway
if you don't have a dedicated security department.
-->

---

##  My framework will protect me from all security threats

<!-- note

Third misconception - My framework will protect me from all security threats

Yes, from some of them. Your framework will protect you on the start, but as application logic grows,
developers will itroduce more vulnerabilities in code and there will be less and less
help from the framework itself.

**NEXT**: So that was about misconceptions about security.
And with that we can now look at the things that we,
as a developers, can do to make our applications more secure.
-->