# Project 9 - Pentesting Live Targets

Time spent: **6** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

Vulnerability #1: SQL Injection

Description: By looking into SQL Injections and finding a list of payloads. I attempted to utilize ```admin" or "1"="1"/*``` to see if the database was vulnerable. While it didn't grant me access, the database does show that an attempt failed which means further testing could lead to better results.

![blue](https://user-images.githubusercontent.com/98777557/164861530-1b30c8c6-7db2-44cc-9fa9-3d70a76e5c43.gif)



## Green

Vulnerability #1: XSS

Description:Using a simple XSS script. We can recreate an attack and see the vulnerability ```<script>alert('XSS')</script>``` was used.

![green](https://user-images.githubusercontent.com/98777557/164861524-738b9292-db38-43ce-a839-424d738d7e83.gif)



## Red

Vulnerability #1:IDOR
Description: We can see IDOR at work when going through the pages. We'll notice that there will be an associated tag with each page. If we modified this tag we can see the vulnerability.

![red](https://user-images.githubusercontent.com/98777557/164861517-8e323053-0cc0-4fe7-976a-14e329225610.gif)



## Notes

Trying to get a more unique XSS to work for Green's site was a bit difficult due to the fact that everyone was on it trying out their own.
