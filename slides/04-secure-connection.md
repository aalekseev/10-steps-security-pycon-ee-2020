<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li className="active">Use secure connection</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
</ol>

<!-- note

On this slide we see a 10 steps checklist that we will be revisiting in the end.
We can see only first item right now, but other items will be revealed as we go,
and a link to the repository with complete steps will be available in the last slides.
We will start with easy to fix things and will go down the topics where automation tools
won't help you that much and you will be feeling scared and alone.

NEXT: The first item in the list might seem even too easy. Like it is 2020, browsers will show
his icon with a lock near the site address to give a hint that site is secure.
-->

---

<!-- sectionTitle: Secure Connection -->

import mitm from '../assets/mitm.png'

## 1. Use secure connection (for everything)

<img src={mitm} className="slide-bottom content-center" />

<!-- note

Well, what is overlooked, is that even if the site itself is served over HTTPS connection,
if parts of it still using insecure HTTP connection to load images, javascript files or stylesheets
you can say that it is not using secure connection.

The resource that is requested via insecure connection can be modified and replaced by
malicious user listening to the traffic in the for example free public WiFi.
This is called a man in the middle attack, and you can see it in the picture.
In this picture attacker is spoofing the secure sertificate and imagine that with
HTTP connection they don't even have to do it.

- https://support.mozilla.org/en-US/kb/mixed-content-blocking-firefox

NEXT: If we have already a valid SSL certificate, what else
we need to check to ensure that our application truly using secure connection?
-->

---

## 1. Use secure connection for everything (fix)

1. Ensure that SSL sertificates are not expired (have a notification when it is)
1. Ensure that on load-balancer or proxy serving all requests via secure connection.
    Also check out `SECURE_SSL_REDIRECT` Django setting
1. Ensure that every image, javascript and stylesheet are server under secure connection as well
1. Ensure that if your application communicate with third-party API it uses a secure connection
1. If your application needs to transfer files via FTP, prefer using SFTP

<!-- note
You can see that there is also mentions of FTP and third-party API connections. And it is here for a reason
- Even if your application security level is pretty good, if part of the system works with less
secure components - it is a weak spot that can be used as an attack vector.

With checking secure connection to our web application, we now sertain at least spoofing on
our application is a bit harder and requires more skills from attacker.
-->