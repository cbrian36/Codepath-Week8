# Project 8 - Pentesting Live Targets

Time spent: **X** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection
* View a any salesperson's profile
* The end of the url should be "id=someInteger"
* Replace the integer with ```' OR SLEEP(10)=0--'``` and press enter
* The webpage should reload after 10 seconds

  - [ ] GIF Walkthrough: ![](https://i.imgur.com/PlGJagH.gif)

Vulnerability #2: Session Hijacking/Fixation
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/MJgbz9K.gif)


## Green

Vulnerability #1: Username Enumeration
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/BqJcyXR.gif)

Vulnerability #2: Cross-Site Scripting
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/esx4HyK.gif)


## Red

Vulnerability #1: Insecure Direct Object Reference
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/dOBXRlO.gif)

Vulnerability #2: Cross-Site Request Forgery
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/6sB7IlD.gif)


## Bonus Objective

Vulnerability: Build on cross-site scripting to dedirect the user to a new URL
  - [ ] GIF Walkthrough: ![](https://i.imgur.com/NMNsFw7.gif)


## Notes

Describe any challenges encountered while doing the work
