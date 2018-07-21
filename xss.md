1.  What's XSS?
2.  XSS vulnerabilities
3.  XSS Goal and Types of XSS
4.  Usual types of attacks
5.  Methods of prevent XSS
6.  XSS Quiz
7.  References

////////// 1. What's XSS?

Cross Site Scripting, otherwise known as XSS is a code injection attack allowing the injection of malicious code into a website.
XSS is currently one of the most common website attacks, with almost every website requiring the user to have JavaScript turned on.
Rather than being an attack on the website itself, it uses the website as a means to attack the users of that website.
When you can get your XSS permanently on a website all those who visit that page will have the JavaScript executed by their browser.

    https://www.youtube.com/watch?time_continue=77&v=k7cGvEwsP6g

////////// 2. XSS vulnerabilities

XSS vulnerabilities are especially dangerous because an attacker exploiting an XSS attack can gain the ability to do whatever the user can do, and to see what the user sees – including passwords, payment and financial information, and more. Worse – the victims, both the user and the vulnerable application, often won’t be aware they’re being attacked.

The possibility of JavaScript being malicious becomes more clear when you consider the following facts:

- JavaScript has access to some of the user's sensitive information, such as cookies.
- JavaScript can send HTTP requests with arbitrary content to arbitrary destinations by using XMLHttpRequest and other mechanisms.
- JavaScript can make arbitrary modifications to the HTML of the current page by using DOM manipulation methods.

////////// 3. XSS Goal and Types of XSS
While the goal of an XSS attack is always to execute malicious JavaScript in the victim's browser, there are few fundamentally different ways of achieving that goal.

XSS attacks are often divided into five types:

a) Stored or Persistent XSS, which is when malicious script is injected directly into the vulnerable application. The malicious string originates from the website's database.
https://www.veracode.com/sites/default/files/styles/media_responsive_widest/public/xss-example-2.gif?itok=5vxqJ3_r

b) Reflected XSS or Non-persistent XSS, which involves ‘reflecting’ malicious script into a link on a page, The attack will activate once the link has been clicked ,where the malicious string originates from the victim's request.
https://www.veracode.com/sites/default/files/styles/media_responsive_widest/public/xss-example-1.gif?itok=b12QvLa2

c) DOM-based XSS, where the vulnerability is in the client-side code rather than the server-side code.
https://1.bp.blogspot.com/-GmNArFk3T_w/WLtyktd1EsI/AAAAAAAAAcQ/udXiMUMeRqsqeLprsq1giRqMvMqOgCKLQCLcB/s1600/DOM-based-xss.png

d) Self-XSS, is a form of XSS vulnerability which relies on Social Engineering in order to trick the victim into executing malicious JavaScript code into their browser. Although it is technically not a true XSS vulnerability due to the fact it relies on socially engineering a user into executing code rather than a flaw in the affected website allowing an attacker to do so, it still poses the same risks as a regular XSS vulnerability if properly executed.

e) Mutated XSS (mXSS) XSS happens, when the attacker injects something that is seemingly safe, but rewritten and modified by the browser, while parsing the markup. This makes it extremely hard to detect or sanitize within the websites application logic. An example is rebalancing unclosed quotation marks or even adding quotation marks to unquoted parameters on parameters to CSS font-family.

////////// 4. Usual types of attacks

Among many other things, the ability to execute arbitrary JavaScript in another user's browser allows an attacker to perform the following types of attacks:

a) Cookie theft
The attacker can access the victim's cookies associated with the website using document.cookie, send them to his own server, and use them to extract sensitive information like session IDs.

b) Keylogging
The attacker can register a keyboard event listener using addEventListener and then send all of the user's keystrokes to his own server, potentially recording sensitive information such as passwords and credit card numbers.

c) Phishing
The attacker can insert a fake login form into the page using DOM manipulation, set the form's action attribute to target his own server, and then trick the user into submitting sensitive information.

Although these attacks differ significantly, they all have one crucial similarity: because the attacker has injected code into a page served by the website, the malicious JavaScript is executed in the context of that website. This means that it is treated like any other script from that website: it has access to the victim's data for that website (such as cookies) and the host name shown in the URL bar will be that of the website. For all intents and purposes, the script is considered a legitimate part of the website, allowing it to do anything that the actual website can.

////////// 5. Methods of prevent XSS
Recall that an XSS attack is a type of code injection: user input is mistakenly interpreted as malicious program code. In order to prevent this type of code injection, secure input handling is needed.

In order to be truly vigilant against XSS and other common, debilitating vulnerabilities, like the rest of the OWASP Top 10, it’s important to use a mix of code review, automated static testing during development and dynamic testing once the application is live, in addition, of course, to using secure coding practices that will help prevent vulnerabilities like cross-site scripting.

For a web developer, there are three fundamentally different ways:

a) Escaping

The first method you can and should use to prevent XSS vulnerabilities from appearing in your applications is by escaping user input. Escaping data means taking the data an application has received and ensuring it’s secure before rendering it for the end user. By escaping user input, key characters in the data received by a web page will be prevented from being interpreted in any malicious way. In essence, you’re censoring the data your web page receives in a way that will disallow the characters – especially < and > characters – from being rendered, which otherwise could cause harm to the application and/or users.

If your page doesn’t allow users to add their own code to the page, a good rule of thumb is to then escape any and all HTML, URL, and JavaScript entities. However, if your web page does allow users to add rich text, such as on forums or post comments, you have a few choices. You’ll either need to carefully choose which HTML entities you will escape and which you won’t, or by using a replacement format for raw HTML such as Markdown, which will in turn allow you to continue escaping all HTML.

b) Validating Input

Expect any untrusted data to be malicious. What’s untrusted data? Anything that originates from outside the system and you don’t have absolute control over so that includes form data, query strings, cookies, other request headers, data from other systems (i.e. from web services) and basically anything that you can’t be 100% confident doesn’t contain evil things.

Validating input is the process of ensuring an application is rendering the correct data and preventing malicious data from doing harm to the site, database, and users. While whitelisting and input validation are more commonly associated with SQL injection, they can also be used as an additional method of prevention for XSS. Whereas blacklisting, or disallowing certain, predetermined characters in user input, disallows only known bad characters, whitelisting only allows known good characters and is a better method for preventing XSS attacks as well as others.

Input validation is especially helpful and good at preventing XSS in forms, as it prevents a user from adding special characters into the fields, instead refusing the request. However, as OWASP maintains, input validation is not a primary prevention method for vulnerabilities such as XSS and SQL injection, but instead helps to reduce the effects should an attacker discover such a vulnerability.

c) Sanitizing

A third way to prevent cross-site scripting attacks is to sanitize user input. Sanitizing data is a strong defense, but should not be used alone to battle XSS attacks. It’s totally possible you’ll find the need to use all three methods of prevention in working towards a more secure application. Sanitizing user input is especially helpful on sites that allow HTML markup, to ensure data received can do no harm to users as well as your database by scrubbing the data clean of potentially harmful markup, changing unacceptable user input to an acceptable format.

////////// 6. XSS Quiz: https://classroom.udacity.com/courses/ud897/lessons/8161938789/concepts/df62aab2-6ca8-4412-9040-f85dbcd8688e

////////// 7. References
https://www.youtube.com/watch?v=M_nIIcKTxGk
https://www.checkmarx.com/2017/10/09/3-ways-prevent-xss/
https://excess-xss.com/
https://www.incapsula.com/web-application-security/cross-site-scripting-xss-attacks.html
https://en.wikipedia.org/wiki/Cross-site_scripting
