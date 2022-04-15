# Unit 7/8 - WordPress Pentesting
Time spent: **78** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities(3 required, 2 optional)** affecting an old version of WordPress.

## Pentesting Report

### WordPress <= 4.2 Cross-Site Request Forgery)CSRF

* Vulnerability types: CSRF
* Tested in version: 3.9
* Fixed in version: 4.1.14

## Summary: 
The current version of wordpress that I am using(3.9) are susceptible to CSRF. Cross-site request forgery (or CSRF) allows an attacker to induce a victim user to perform actions that they do not intend to.

### Gif Walkthrough:![CSRF](https://user-images.githubusercontent.com/98777557/163623803-5495047c-12ad-42cb-a0e1-77c7fecae35b.gif)


### Steps to recreate: 
First, a post is created. After the post is made, we then go to the replies/comments. Posting a comment with the line ```<script>alert(document.cookie)</script>```,
The code will execute bringing up a pop-up with cookie data.

### Affected source code:

*  https://wpscan.com/vulnerability/e080c934-6a98-4726-8e7a-43a718d05e79
* https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5492
* https://github.com/WordPress/WordPress/commit/03e5c0314aeffe6b27f4b98fef842bf0fb00c733
* https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/



### WordPress <= 4.2 Password Enumeration
* Vulnerability types: Brute-Force
* Tested in version: 3.9

### Summary: 
Wordpress is vulnerable to password and username enumeration. A series of brute-force techniques are used to confirm valid user accounts in the system.

### Gif Walkthrough:![passwordenum](https://user-images.githubusercontent.com/98777557/163623780-5c077ab6-2e3c-4762-83ef-364bb377e7cf.gif)


### Steps to recreate:
After running the command to scan for usernames. We place those names into a document called "usernames.txt". Bringing up the terminal, we insert the command ```wpscan --url http://127.0.0.1:8080 --api-token YOUR_TOKEN --usernames username.txt --passwords password.txt.``` Our passwords have already been placed into the document with several others. We run the command, and WPscan matches up the passwords with the proper account through bruteforce.

### WordPress <= 4.1.1 - Unauthenticated Stored Cross-Site Scripting (XSS)
* Vulnerability types: XSS
* Tested in version: 3.9
* Fixed in version: 4.1.2

### Summary: 
Wordpress is vulnerable to Cross-Site Scripting from post, comment, or url. 

### Gif Walkthrough:![xss v2](https://user-images.githubusercontent.com/98777557/163623828-c51ce993-d1fd-4cb9-83e6-415b6045f3dc.gif)


### Steps to recreate:
First, a post is created. After the post is made, we then go to the replies/comments. Posting a comment with the line 
```<var onmouseover="prompt(1)">On Mouse Over</var>```. Upon refresh we then move the cursor over the line allowing the pop-up to initiate.
### Affected source code:

* https://wpscan.com/vulnerability/604b553d-5492-4f8c-af7a-db7169780032
* https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-3438
* https://wordpress.org/news/2015/04/wordpress-4-1-2/
* https://cedricvb.be/post/wordpress-stored-xss-vulnerability-4-1-2/
