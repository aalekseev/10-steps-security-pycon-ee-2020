<!-- classes: ten-steps -->

## 10 Steps

<ol>
    <li>Use secure connection</li>
    <li>Configure software with security in mind</li>
    <li className="active">Don't commit secrets to the repository</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
    <li>?</li>
</ol>

<!-- note
One of the easy to miss things is commiting the secret codes,
password or other sensitive information to the version control.
-->

---

<!-- sectionTitle: Secrets -->

import commitingSecrets from '../assets/commiting-secrets.jpg'

## 3. Don't commit secrets to the repository

#### 2 600 000 results on GitHub containing "SECRET_KEY" word

<img src={commitingSecrets} className="slide-bottom content-center" />

<!-- note

What will happen if we commit and push our code with SECRET_KEY
or any other sensitive data like password to the email service,
in plain text to the remote repository in GitHub, GitLab or Bitbacket?

Once something enters the internet, it is really hard to remove it.
It is a bit scary, I searched in github word "secret key" and
it shows 2.5M results for only python code and for only "SECRET_KEY" keyword.

In this case we are looking at commited secret keys to Django
application. With this string of characters Django creates password reset tokens,
protects session data and create random session keys and more.

**NEXT**: If we checked our project and found out that secret key to access 
your email provider was commited to the repository - what will be the next steps?
-->

---

## 3. Don't commit secrets to the repository (fix)

1. Create a new secret key
1. Use environment variables to store it
    - For Django we use [Django-environ](https://django-environ.readthedocs.io/en/latest/)
1. Remove the old secret key from Git history (if possible)
    - Requires to mess around with Git reflog and might be dangerous
1. Redeploy the application

<!-- note

The good news is that external automatic tools, that we will be looking into
a bit later, can detect this and will notify us, _if we will use the tools_.

But in short, the secret key needs to be invalidated as soon as possible
but creating a new one, storing it securely and re-deploying the application
so this key can't be used any longer.

Next topic is a bit related as well to the overall software configuration and managing, rather than
actual development.
-->