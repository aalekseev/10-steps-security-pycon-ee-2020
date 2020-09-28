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
    <li className="active">Don't trust user input and sanitize it</li>
    <li>?</li>
    <li>?</li>
</ol>

---

<!-- sectionTitle: User Input -->

## 8. Don't trust user input and sanitize it

- [№1 in OWASP Top 10 - Injection](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A1-Injection)
- [№4 in OWASP Top 10 - XML External Entities (XXE)](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A4-XML_External_Entities_(XXE))
- [№7 in OWASP Top 10 - Cross-Site Scripting XSS](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS))
- [№8 in OWASP Top 10 - Insecure Deserialization](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)

### Not all users are nice.

<!-- note
User input can take many forms
- A comment form under the blog post
- A user profile image that user uploads themself
- An XML file that user to upload some data

But what is common theme - is that not all users are nice, and they will not do what they "suppose"
to do with your application.

**NEXT**: So - 2 most common attacks Cross-site scripting and SQL injection
-->

---

import xssTweetdeck from '../assets/xss-tweetdeck.jpg'

## 8. Don't trust user input and sanitize it (XSS)

<img src={xssTweetdeck} className="slide-bottom content-center" />

<!-- note

So the story goes that there is a popular at that time application Tweetdeck, that many people
and celebrities used to manage multiple twitter accounts. And one day one smart person tried to
post a tweet with javascript code inside. And it worked. After that if you saw that tweet and hit
like or retweet you would be greet with an alert - hey there is a XSS vulnerability in Tweetdeck.
Luckily it was not a malicious user otherwise cosiquences would be far more dangerous.

In the essence cross site scripting related to unsanitized user input on the client side of the
application. Most of the time this attack is most powerful when the code that one user submitted
application rendered is visible to other users.
Typical XSS attacks include session stealing, account takeower, key logging.
-->

---

## 8. Don't trust user input and sanitize it (XSS prevention)

1. From Django 1.0 - template system by default escapes html code
1. Fromt Django 2.1 you can use `json_script` to add JSON safely into template
1. If you can, use markdown instead of raw HTML to provide users with reach text editor
1. But other than that - check your templates for user input and if it was marked as safe (in which case it is UNsafe)

<footer className="content-right">
    <a href="https://tonybaloney.github.io/posts/xss-exploitation-in-django.html">Anthony Shaw - XSS Exploitation in Django</a>
</footer>

<!-- note

Here are some of the things that you can do, to prevent the XSS attack in Django application.

And a super cool in-depth article by Anthony Shaw about XSS in Django and btw he is an author of this
Pycharm security plugin.

SHOULD SKIP?
May 2020, XSS in Log-in with facebook button
https://wiraltech.com/xss-vulnerability-in-login-with-facebook-button-pays-usd20000-bounty/

**NEXT**: So this was about a user input displayed on client side
and now let's look at more dangerous server side unsanitized user input
-->

---

## 8. Don't trust user input and sanitize it (SQLi)
- [№1 in OWASP Top 10 - Injection](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A1-Injection)

- First attack [Feb 2002](https://www.securityfocus.com/news/346) (18 years ago)
- Recent one - [August 2020](https://www.bleepingcomputer.com/news/security/freepik-data-breach-hackers-stole-83m-records-via-sql-injection/
), Freepick SQL injection 83 000 000 user records stolen

<img src={"https://imgs.xkcd.com/comics/exploits_of_a_mom.png"} className="slide-bottom content-center large-picture" />

<!-- note

SQL injection. This is a number 1 in OWASP top 10, most popular and most dangerous attack.
The threat is that user with malicious intent can provide a harmful input to the server,
and server will execute the code on the Database level.
Any user can read/change sensible data in the database. And even though this attack is known for
almost **20** years

And a classical XKCD comics about it

In this example we are looking into SQL injection, but it can be URL paramethers, request
headers, cookies, JSON, XML data inputs.

**NEXT**: Ok, this is a scare and old attack vector, what can we do about it?
-->

---

## 8. Don't trust user input and sanitize it (SQLi example)

```python
# Malicious SQL code, will return all rows from the
# db table regardless of initial filter in your SQL code
user_input = '"" or 1 = 1;--'

# BAD
# Note that we are formatting the string here, before passing it to Django
Customers.objects.raw(
    f'SELECT * FROM Customers WHERE customer_name = {user_input}'
)

# BETTER
# Note that here we passing malicious output to the Django,
# rather than formatting the SQL code ourself.
# Postgres is smart enough to escape malicious input and not evaluate it.
Customers.objects.raw(
    'SELECT * FROM Customers WHERE customer_name = %s',
    [user_input]
)
```

---

## 8. Don't trust user input and sanitize it (SQLi prevention)

1. Use Django ORM
    ```python
    user_input = '"" or 1 = 1;--'
    Customers.objects.filter(customer_name=user_input)
    ```
1. If you can't - pass argumets instead of formatting the string
    ```python
    user_input = '"" or 1 = 1;--'
    Customers.objects.raw('SELECT * FROM Customers WHERE customer_name = %s', [user_input])
    ```
1. Run automatic tools regularly to be notified about unprotected SQL formatiing

<!-- note

Django ORM is your security blanket here, it will sanitize the user input for you.
However if you provided it with SQL query with user input already there,
there is not much Django can do about it.

Using Django ORM might not be possible in some situations - for example
legacy code with huge 200 lines SQL statement that nobody understands anymore
and it was not updated for 5 years.
In this case it is totally fine to pass user input as paramethers,
that way it also will be sanitized and escaped by Django and the database.

**Next**: Brave yourself, 2 more steps and we are nearly at the end of the talk,
 going into I would say creative topics
-->