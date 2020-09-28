<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li>Use secure connection</li>
    <li>Configure software with security in mind</li>
    <li>Don't commit secrets to the repository</li>
    <li>Check application dependencies</li>
    <li className="active">Make it harder for attackers to guess about your application</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
</ol>

<!-- note
NEXT: As a next step, let's see how we can make it harder for attacker to
gather information about our application 
-->

---

<!-- sectionTitle: Guessing -->

import guessing from '../assets/secure-security.jpg'

## 5. Make it harder for attackers to guess about your application

- Can you guess how many users in the system, given that you registered just now? `https://mysite.com/api/v1/profile/users/21/`
- Can you guess the admin login page? `https://mysite.com/admin/`
- Can you guess the admin email? `admin@mysite.com`

<img src={guessing} className="slide-bottom content-center" />

<!-- note

- How hard it is to guess admin login page to make a brute-force attack
    trying well-known vulnerable passwords?
- How hard it is to guess the Django version of the application, to try to perform
    a vulnerability that was not patched in that version?

**NEXT**: Let's look on the next slide how we can improve situation a little bit,
but keep in mind, this is not to stop the attack but rather
to make exploring our application not a walk in the park.
-->

---

## 5. Make it harder for hackers to guess about your application (fix)

1. Change the default admin dashboard url
1. Use other references for objects than ID from the database
1. Check that you are not leaking in plain text information about your system
    in error messages, logs, emails

<!-- note

Changing the admin URL can really make a long way and difference. Most automatic
tools that scans for admin urls on sites have a predefined dictionary of keywords that they use,
and if you are a harder target, the attacker might just skip you application.

And remember all these cases when username and password in plain text was sent over email?

We talk a bit about configuration of the application, and I mentioned some tools that
are available to automatically get reports about some of the vulnerabilities. Two next steps are about
the tools.
-->