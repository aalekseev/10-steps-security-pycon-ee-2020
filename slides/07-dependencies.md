<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li>Use secure connection</li>
    <li>Configure software with security in mind</li>
    <li>Don't commit secrets to the repository</li>
    <li className="active">Check application dependencies</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
</ol>

<!-- note
Let's talk about application dependencies!
-->

---

<!-- sectionTitle: Dependencies -->

## 4. Check application dependencies

- [№9 in OWASP Top 10 - Using Components with Known Vulnerabilities](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities)
- [Aug 2020, Malicious JS library that was stealing sensitive files removed from NPM](https://securityaffairs.co/wordpress/107691/malware/npm-package-fallguys-removed.html)

<img src={"https://www.monkeyuser.com/assets/images/2019/116-library-unboxing.png"} className="slide-bottom content-center" />

<!-- note

Libraries are written by people. And people make mistakes, or intentionally do bad things.

In the link on the slide is a recent case when library was stealing personal data under the hood.
Luckily it was shut down fast. The other important thing related to libraries is that they
usually have new versions with patched vulnerabilities which we should use.

And it is a responsibility of the developer to frequently check and update library versions and setup
notifications about new versions.

There is a lot of automatic tools that make having notifications
about new secure versions easy to receieve.
-->

---

## 4. Check application dependencies (fix)

```
(venv) ➜  django_app safety check --full-report
+==============================================================================+
| REPORT                                                                       |
| checked 40 packages, using default DB                                        |
+============================+===========+==========================+==========+
| package                    | installed | affected                 | ID       |
+============================+===========+==========================+==========+
| insecure-package           | 0.1.0     | <0.2.0                   | 25853    |
+==============================================================================+
| This is an insecure package with lots of exploitable security                |
| vulnerabilities.                                                             |
+==============================================================================+
| django                     | 1.11      | <1.11.19,>=1.11.0        | 36885    |
+==============================================================================+
| Django 1.11.x before 1.11.19 allows Uncontrolled Memory Consumption via a    |
| malicious attacker-supplied value to the django.utils.numberformat.format()  |
| function.                                                                    |
+==============================================================================+
```

<!-- note

Here we can see an example of the full report of python `safety` package, it can not only
show insecure versions but also short explanation.

See that here mentioned that some numeric template filters in Django
can comsule a lot of application memory which can be used for denial of service attack.
An intent of the Denial od service attack or more common known as DDoS is
to temporary or permanently make application unavailable for users.

This dependency check can be setup to run each time you push changes to the repository,
or even better, to run periodically and send for example emails when new
more secure version of the library is available.
-->
