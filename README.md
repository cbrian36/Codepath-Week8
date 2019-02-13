# Project 8 - Pentesting Live Targets

Time spent: **5** hours spent in total

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
* The end of the url should be ```id=someInteger```
* Replace the integer with ```' OR SLEEP(10)=0--'``` and press enter
* The webpage should reload after 10 seconds

- [ ] GIF Walkthrough: ![](https://i.imgur.com/PlGJagH.gif)

Vulnerability #2: Session Hijacking
* Use two browsers: Chrome (target) and Firefox (attacker)
* Login to the target and navigate to ```public/hacktools/change_session_id.php``` to get the session ID
* Attacker navigate to ```public/hacktools/change_session_id.php``` and change the session ID to the target's session ID
* Attacker should be able to login without entering a username and password

- [ ] GIF Walkthrough: ![](https://i.imgur.com/MJgbz9K.gif)


## Green

Vulnerability #1: Username Enumeration
* Note that ```pperson``` and ```jmonroe99``` are both valid usernames
* Trying to login using a valid username and invalid password will result in a bolded error message
* However trying to login with an invalid username and password will result in a non-bolded error message
- [ ] GIF Walkthrough: ![](https://i.imgur.com/BqJcyXR.gif)

Vulnerability #2: Cross-Site Scripting
* In the Contact section you can add an alert script
* This alert will be triggered when a logged-in user visits the feedback section
- [ ] GIF Walkthrough: ![](https://i.imgur.com/esx4HyK.gif)


## Red

Vulnerability #1: Insecure Direct Object Reference
* View any salesperson's profile (do not log in)
* You can view hidden profiles by changing the ID value at the end of the URL
* Specifically salespeople with IDs 10 and 11 should not be accessible to those not logged in
* When the ID value is modified to 10 or 11 in the green and blue websites, the site redirects to the territories.php page corresponding to the heading "Find a Salesperson"
- [ ] GIF Walkthrough: ![](https://i.imgur.com/dOBXRlO.gif)

Vulnerability #2: Cross-Site Request Forgery
* Submit a link to the following malicious webpage in the Contact section
```
<html>
  <head>
    <title>Feedback</title>
  </head>
  <body onload="document.CSRF.submit()">
	<form action="https://35.184.88.145/red/public/staff/salespeople/edit.php?id=4" method="post" style="display: none;" name='CSRF' target="res">
	    <input type="text" name="first_name" value="No Longer Robert" />
      	<input type="text" name="last_name" value="HACKED" />
      	<input type="text" name="phone" value="123-456-789" />
      	<input type="text" name="email" value="who@HACKED.com" />
	</form>
    <iframe name="res" style="display: none;"></iframe>
  </body>
</html>
```
* This page will silently submit a form to edit the information of salesperson Robert Hamilton
* This form submission will only occur when a logged-in user views the feedback section and navigates to the link provided
- [ ] GIF Walkthrough: ![](https://i.imgur.com/6sB7IlD.gif)


## Bonus Objective

Vulnerability: Build on cross-site scripting to dedirect the user to a new URL
* This exploit uses the same Cross-Site Scriping idea shown above but instead of showing an alert popup it will redirect the user to a new webpage
* The redirection is achieved by using ```window.location.assign("url")```
- [ ] GIF Walkthrough: ![](https://i.imgur.com/NMNsFw7.gif)


## Notes
