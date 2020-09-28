<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li>Use secure connection</li>
    <li>Configure software with security in mind</li>
    <li>Don't commit secrets to the repository</li>
    <li>Check application dependencies</li>
    <li>Make it harder for attackers to guess about your application</li>
    <li className="active">Research and use the tools that already available</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
</ol>

<!-- note
I decided to split them into to because some of the tools can be hard to install
and use on corporate PC, and there is tools that comes out of the box with Django.
-->

---

<!-- sectionTitle: Tools -->

## 6. Research and use the tools that already available

1. Run django deploy check `python manage.py check --deploy`
1. Manage user access with `user_passes_test` and `permission_requred`
1. Manage allowed methods with `require_safe`, `require_POST`
1. When you need to compare two strings securely use [`constant_time_compare`](https://github.com/django/django/blob/master/django/utils/crypto.py#L77)
1. When you need to securely sign some data and verify it later, use [`signing`](https://docs.djangoproject.com/en/3.1/topics/signing/) module
1. To prevent sensitive data being leaked into application logs, use [`sensitive_variables`](https://github.com/django/django/blob/d8e233352877c37c469687287e7761e05bdae94e/django/views/decorators/debug.py#L6) decorator
1. To protect POST paramethers being leaked into application logs, use [`sensitive_post_paramethers`](https://github.com/django/django/blob/d8e233352877c37c469687287e7761e05bdae94e/django/views/decorators/debug.py#L47) decorator
1. If you need to render JSON to template use `json_script`

<!-- note

For example Django comes with a lot of tools out of the box, you
as a developer just need to be avare of them and use accordingly.

Here are some examples that I found mentioned on the internet. To be honest,
I did not knew about half of them, and only during research phase found out about them.
And some of the utility functions are not metioned in the official documentation, but since 
Django is opensource you can and should look into source code and see what useful
helper functions Django can provide you.

One of the interesting tools is constant time comapre. It is related to the side-channel attacks. This
is a type of attack that is based on measuring how much time each computation (in this case comparing two strings)
will take.

**NEXT**: Now when we looked into built-in tools, lets see what extra tools that might be harder to install
in some workspaces but definately will make our lives easier.
-->

---

<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li>Use secure connection</li>
    <li>Configure software with security in mind</li>
    <li>Don't commit secrets to the repository</li>
    <li>Check application dependencies</li>
    <li>Make it harder for attackers to guess about your application</li>
    <li>Research and use the tools that already available</li>
    <li className="active">Use automatic tools to check your application</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
</ol>

---

## 7. Use automatic tools to check your application

- [OWASP ZAP](https://www.zaproxy.org/)
- [Pycharm Python security plugin](https://pycharm-security.readthedocs.io/en/latest/)
- [Pipenv check](https://pipenv.pypa.io/en/latest/advanced/#detection-of-security-vulnerabilities)
- [Bandit](https://github.com/PyCQA/bandit)
- [Django-security app](https://github.com/sdelements/django-security)
- [Django defender](https://github.com/jazzband/django-defender)
- [Django CSP](https://github.com/mozilla/django-csp)
- [Django XSS fuzzer](https://github.com/tonybaloney/django-xss-fuzzer)
- [Mozilla Observatory](https://observatory.mozilla.org/)

<!-- note

1. **OWASP ZAP**
    - This is an attack proxy. It sits between browser and application, intercepts requests, analyzes it for vulnerabilities and puts a report
        with links to OWASP documentation
1. **Pycharm python security plugin**
    - The plugin looks at your Python code for common security vulnerabilities and suggests fixes. This is all-purpose plugin, not only for web-developers
    - It can automatically check with some extent for SQL injection, XSS and misconfiguration
1. **Pipenv check**
    - If you are using Pipenv to lock project dependencies, it provides a command to check your dependencies graph and check for vulnerabilities in package versions
1. **Bandit**
    - A tool that checks for security vulnerabilities and reports commited secrects, using raw SQL in Django but also lots of all-purpose security checks
1. **Django-security app**
    - Provides number of models, views, middlewares and forms to facilitate security hardening of Django applications.
1. **Django defender**
    - A simple Django reusable app that blocks people from brute forcing login attempts.
1. **Django CSP**
    - Add content security policy - aloowing to speciafy from where exactly your site is allowed to load any media, static and javascript files
1. **Mozilla Observatory**
    - Automatic tool that checks cookies, and request headers and a few other cheecks

Now we slowly coming to a more hard problems.
-->