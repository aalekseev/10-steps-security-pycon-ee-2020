<!-- sectionTitle: Misconceptions -->
import unicorn from '../assets/unicorn.png'

## Misconceptions about Security

### Secure Web Application

<img className="content-center slide-bottom" src={unicorn} />

<p><small>
Image from <a href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2007266">Pixabay</a>
</small></p>

<!-- note

Right from the start let's be transparent about it - there is no such thing as secure system.
No system is 100% secure, and everything is mostly broken.

NEXT: With this out of the way, there are a few more topics that I would like to
clear out. In my opinion security problems so often related to people rather than code
that talking about security mindset is as important as stories about
cool vulnerabilities.
-->

---

## Misconceptions about Security

### It is a job for _**only**_ security professionals

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

## Misconceptions about Security

### Security is **_too complex_** to learn about

<!-- note

Second misconception - Security is too complex to learn about

Well it is hard to learn about, especially cryptography, this stuff is hard.
But at the same time, there are basic steps, if followed, that will make
your web application better protected than vast majority of sites.

Amature hackers looking for an easy target, and if you put some
effort and thought about security you already doing better than the rest of the
applications out there.
-->

---
## Misconceptions about Security

### My **_framework will protect me_** from all security threats

<!-- note

Third misconception - My framework will protect me from all security threats

Django has a reputation of a very secure framework, this is what we are proud of.

Yes, your framework will protect you on the start, but as application logic grows,
developers will itroduce more vulnerabilities in code and there will be less and less
help from the framework itself.

**NEXT**: So that was about misconceptions about security.
And with that we can now look at the things that we,
as a developers, can do to make our applications more secure.
-->