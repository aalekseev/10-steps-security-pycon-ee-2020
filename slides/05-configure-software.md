<!-- classes: ten-steps -->

## 10 steps for more<br />secure applications

<ol>
    <li>Use secure connection</li>
    <li className="active">Configure software with security in mind</li>
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
Let's talk about configuration. It is also seem like an obvious thing to do,
but this vulnerability is listed in top 10 vulnerabilities for years,
and it is pretty important topic to talk about.
-->
---

<!-- sectionTitle: Software Configuration -->

import djangoErrorPage from '../assets/django-error-page.jpg'

## 2. Configure software with security in mind

- [№6 in OWASP Top 10 - Security Misconfiguration](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A6-Security_Misconfiguration)
- [№10 in OWASP Top 10 - Insufficien Logging and Monitoring](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A10-Insufficient_Logging%252526Monitoring)

<img src={djangoErrorPage} className="slide-bottom content-center" style={{width: "130%", height: "130%"}} />

<!-- note

But first, you can see two links to the OWASP top 10. What is it?

https://owasp.org/www-project-top-ten/

OWASP - short for Open Web Application Security Project.
It is a nonprofit foundation that research and publish 10 most common security vulnerabilities in Web Applications.
And in this year 2020 we have 2 vulnerabilities that, at least in my mind, connected to each other.
One is misconfiguration and another is insufficient monitoring which basically means that
your system was not configured to alert you about suspicious activities - in other words you won't know
when you were hacked.

So, talking about misconfiguration - on the screenshot you see a Django debug page, it
intended for local development and shows lots of information:
- Python version, Django version, Path to the application on your server

This is intended for the local environment, and super helpful for developer. 

I hope that it is clear, that with this information the attacket at least can Open
django releases page, and look for a simple vulnerabilities that can be performed on Django
sites with verison lower than listed here. How do we fix that?
-->

---

## 2. Configure software with security in mind (fix)

```console
$ python manage.py check --deploy
System check identified some issues:

WARNINGS:
?: (security.W004) You have not set a value for the SECURE_HSTS_SECONDS setting. If your entire site is served only over SSL, you may want to consider setting a value and enabling HTTP Strict Transport Security. Be sure to read the documentation first; enabling HSTS carelessly can cause serious, irreversible problems.
?: (security.W008) Your SECURE_SSL_REDIRECT setting is not set to True. Unless your site should be available over both SSL and non-SSL connections, you may want to either set this setting True or configure a load balancer or reverse-proxy server to redirect all connections to HTTPS.
?: (security.W012) SESSION_COOKIE_SECURE is not set to True. Using a secure-only session cookie makes it more difficult for network traffic sniffers to hijack user sessions.
?: (security.W016) You have 'django.middleware.csrf.CsrfViewMiddleware' in your MIDDLEWARE, but you have not set CSRF_COOKIE_SECURE to True. Using a secure-only CSRF cookie makes it more difficult for network traffic sniffers to steal the CSRF token.
?: (security.W018) You should not have DEBUG set to True in deployment.
?: (security.W020) ALLOWED_HOSTS must not be empty in deployment.

System check identified 6 issues (0 silenced).
```

<!-- note

One simplest thing that we can do, and what (for example) Django is providing to
us out of the box - is a deploy system check.

We can see on this slide the output of this check.
With the command `python manage.py check --deploy` Django will run a set of
security checks and report you with things that you need to pay attention to.

But configuring software and servers is a much broader topic, which cannot fit
into this presentation. The only advice here is to read carefuly sonftware confguration
manuals and regularly checking that indeed conftware is configured properly.
-->