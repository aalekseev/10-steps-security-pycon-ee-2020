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
    <li className="active">Protect user data by requesting only what necessary</li>
    <li>?</li>
</ol>

---

<!-- sectionTitle: Sensitive Data -->

import sensitive from '../assets/sensitive.png'

## 9. Protect user data by requesting only what necessary 

- [№3 in OWASP Top 10 - Sensitive Data Exposure](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A3-Sensitive_Data_Exposure)
- [Sep 2020, Spreadsheet on the server with 600 000 users with billing history and much more](https://techcrunch.com/2020/09/23/new-york-sports-clubs-owner-breach/)
- [May 2020, major European Bank leaks sensitive data on their website](https://cybernews.com/security/one-of-biggest-european-banks-leaking-sensitive-data-on-website/)

<img src={sensitive} className="slide-bottom content-center" />

<!-- note

Year 2020, one recent case is a gigantic spreadsheet with customer information in plain text laying around
unprotected on the vulnerable server.

The second case is European bank leaking account id and api key to the Cloudfront - a content delivery service.
It is used to speed up access to large media files such as PDF documents. And with the leaked keys malicious user would potentially
be able to download lots of documents with most likely uprotected bank data or change the documents to swap bank account details
in them to steal some real money.

Protecting sensitive data is super important,
so what should we do when we need to work with sensitive data?
-->

---

## 9. Protect user data by requesting only what necessary (example)

```python
# BAD
class UserProfileSerializer(serializers.ModelSeriazlier):
    class Meta:
        model = UserProfile
        fields = "__all__"

# BETTER
class UserProfileSerializer(serializers.ModelSeriazlier):
    class Meta:
        model = UserProfile
        # Note that we explicitly saying which data will
        # be exposed in the application API
        fields = ("profile_pic", "job_title")
```
<!-- note
In this code example we see a declaration of how database model will be converted
to a Python datastructure, which will be rendered as a JSON in an server API response.

In the upper example you see a lazy code where you are not specifying database model fields,
you just telling the frameowrk to expose everything from the DB.
In the better profile serializer you carefully decided and
explicitly saying which fields you would like to expose in the API.

Carefully deciding and explicitly enabling the data that got exposed to the API is a key components here.
-->

---

## 9. Protect user data by requesting only what necessary (preventing)

Django nor any automated tool can protect you from making mistakes here.

However these basic things can help:

- Carefuly decide what data will be exposed in API
- Mask the data in the API if possible
- Don't store sensitive data "just in case"
- Make sure that if you are collecting sensitive data it is encrypted
- All sensitive data should be transmitted only via secure connection
- Disable caching for responses that contain sensitive data

<!-- note
How do we prevent data to be leaked?

I would say that the firs point in the list about deciding what data will be exposed is most critical one
in most of the cases. Because it is simple a question - do we really need to store this data? And it is most likely
that it is a "nice to have" rather than strict requirement. And if it is strictly needed to save you home address for example,
then the data needs to be masked and ecrypted.
-->