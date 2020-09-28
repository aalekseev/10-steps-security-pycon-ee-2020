<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li>Use secure connection</li>
    <li>Configure software with security in mind</li>
    <li>Don't commit secrets to the repository</li>
    <li>Check application dependencies</li>
    <li>Make it harder for attackers to guess about your application</li>
    <li>Research and use the tools that already available</li>
    <li>Use automatic tools to check your application</li>
    <li>Don't trust user input and sanitize it</li>
    <li>Protect user data by requesting only what necessary</li>
    <li className="active">Disallow everything, and granually add permissions as they are required</li>
</ol>

<!-- note
So we talked about sensitive data, and this topic is tightly coupled with next and maybe last step - access control. It is coupled in a
way that having a good access control allow you to leak less sensitive data, because you restricting who allowed to see and do what.
-->

---

<!-- sectionTitle: Access Control -->

import access from '../assets/access.jpg'

## 10. Disallow everything, and granually add permissions as they are required

- [№5 in OWASP Top 10 - Broken Access Control](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A5-Broken_Access_Control)

**Authenticated** vs **Authorized**

<img src={access} className="slide-bottom content-center" />

<span>Photo by <a href="https://unsplash.com/@jyoung?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Jonathon Young</a> on <a href="https://unsplash.com/s/photos/gates?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>


<!-- note

Sometimes we check that user is authenticated
(which means they have account in our system and logged in when doing some action),
but never checking that user authorized (which means that they allowed to do specific thing in our system).

What is so dangerous with that you would ask? It starting to be interesting when regular user can do
things that only admin users would ideally be allowed to do. It leads to data vandalism in the best case
scenario - when changing the main page content to contain offencive wording.
It also can result in stealing personal data and many more dangers.

Let's look at the code example
-->

---

## 10. Disallow everything, and granually add permissions (example)

```python
# BAD
def transfer_money_view(request):
    if not request.user.is_authenticated:
        raise PermissionDenied

    form = TransferMoneyForm(request.GET or request.POST)
    if form.is_valid():
        form.save()

    return HttpResponseRedirect(reverse("home"))

# BETTER
def transfer_money_view(request):
    if not request.user.is_authenticated:
        raise PermissionDenied

    # Note that we also check that user
    # allowed to make the action
    if not canTransferMoney(request.user):
        raise PermissionDenied

    form = TransferMoneyForm(request.GET or request.POST)
    if form.is_valid():
        form.save()

    return HttpResponseRedirect(reverse("home"))
```

<!-- note

Why the second example is better? Because there are multiple factors why
user might not be allowed to do a money transfer and we are checking for it.
User can be unverified, or have suspicious transfer history, or be inactive
in the system.

On the next slide I am mentioning some of the things that can be done to
make the system less broken with access control.
-->

---

## 10. Disallow everything, and granually add permissions (preventing)

1. Properly apply access permissions by creating specific user roles and checking allowed actions for each user
2. Make testing user permissions a regular activity, so you would know when acess control is actually broken
3. Follow the simple motto that it is best to disallow everything, and granually add permissions for different user roles

<!-- note

Ok, so we covered all 10 steps - woho! congratulations!
However there is one thing that is super important and kinda missing - because
without it, all other steps simply won't work.
-->