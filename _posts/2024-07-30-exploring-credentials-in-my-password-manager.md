---
title: Exploring credentials in my password manager

layout: post
date: 2024-7-30
author: Daniel
tags:
    - password manager
---
## My history with password managers
I've used password managers since 2014, from LastPass and Dashlane to the Chrome password manager and macOS' Keychain. I'm generally a happy password manager user, appreciating the many great features and convenience. However, over time, as I notice product quality issues, I begin to worry.

One of my favorite features of password managers provides a high-level view of the state of the passwords stored. It highlights aspects that can be improved, such as password strength, password reuse, compromised passwords, and the use of multi-factor authentication.
Recently, the list of reused or weak passwords showed inconsistent results, regardless of whether I used the Android, iOS, or browser apps. In one instance, the Android app alerted me of a password that I allegedly reused tens of times, and, in a different case, the list of weak passwords contained passwords that were not weak at all.

I contacted support with the issues. An excerpt of their response:

> "This issue has been reported internally. While I can assure you that this is on our road-map, I'm afraid I do not yet have an accurate ETA to communicate. Please bear with us as we do our best to address your issue in a timely fashion."

I appreciate the response, but I expect more than an acknowledgment of the issue to maintain my confidence in the product. A password manager has sensitive information, and confidence and trust are essential. Within a week, I canceled my family subscription, which was up for renewal in February, and signed up for 1Password.

## Reasons to use a password manager
When I started using password managers the premise was simple: use a strong and unique password for each service and store it in the password manager so you don’t have to remember it. It took me a while to fully trust the vendor I had chosen (LastPass). For a few months, I used it to store credentials for trivial things and once I was convinced, I used it for everything.

Over time, password managers gained new feature: use of multi-factor authentication, alerts when a stored password is found in a leak, or reused, or it is not considered strong. Whenever the topic of passwords comes up in conversation with friends and family, this is more or less, what I tell them:

### Password strength
A strong password is long, uses random characters, and avoids personal or easy-to-guess information. This increases the difficulty of cracking the password through various attack methods, including brute-force attempts, dictionary attacks, and more sophisticated techniques.

Increasing the length and complexity of a password exponentially increases the time required to crack it. As a user, using long, random passwords and enabling Multi-Factor Authentication (MFA) are effective defenses. Service providers can implement measures such as account lockouts and strong password storage practices.

### Password reuse
When a password is reused across multiple accounts, a single compromised account can lead to multiple security breaches. This enables a type of attack called credential stuffing, where attackers use stolen username and password combinations to attempt access to various services.

To mitigate this risk:
1. Use unique passwords for each account.
2. Enable multi-factor authentication (MFA) when available.
3. Use a password manager to generate and store complex, unique passwords.
4. Stay informed about data breaches and change passwords promptly if compromised.

Password managers solve the problem of remembering numerous unique passwords and often provide additional security features like MFA capabilities.

### Compromised passwords
Cybersecurity is a game of cat and mouse where engineers in charge of the security of a system are constantly racing the bad actors trying to gain access to such systems. Some data breaches happen by pure luck or coincidence, some require malicious insiders, and some are the product of meticulous work of patient people.

If you spend long enough online, you will eventually receive an email warning about a data breach and advising or even requiring you to change your password. You may read about it in the news, or you may somehow find yourself in "Have I Been Pwned?". In any case, a compromised password should be addressed sooner rather than later. The action to take in this case is straightforward: change the password ASAP!

### Multi-Factor Authentication
Multi-factor authentication improves account security by requiring two or more verification methods. These typically combine something you know (a password) with something you have (a phone) or something you are (a fingerprint). Many modern password managers integrate MFA capabilities, allowing them to generate and store time-based codes or support hardware security keys. This integration makes implementing MFA across multiple accounts more convenient, encouraging wider adoption of this crucial security practice.

## A security-minded project
Once I completed the migration from Dashlane to 1Password, I analyzed the contents of my Dashlane data export, specifically, the credentials.csv file. Before I decided to migrate to 1Password, I had already spent a few days cleaning and improving the password health score by eliminating duplicates and changing a few passwords.

I do not have exceptional password hygiene, but I have worked on improving it. I've done my best. I set up MFA for the critical services, whether it is a Yubi key, an authenticator app, or SMS if no other option is available.

For this exploration, I have three goals:
1. Strengthen my passwords
2. Eliminate duplicates
3. Identify accounts or services that I no longer need and deactivate or delete such accounts

## Exploring the data export

### Password reuse
The Dashlane data export contains several CSV files. One of the files is of interest in this case: credentials.csv.

The file has 609 entries, which is unsurprising considering that I've used a password manager for ten years.

Out of 609 credentials in the file, there are:
* 477 unique passwords. Good. We don't want to use them more than once.
* 54 passwords are used two times. This can be improved. However, I suspect the primary issue is duplicate entries for the same service.
* 5 passwords that are used three times. Problematic.
* 1 password repeated four times. Problematic.
* 1 password repeated five times. Problematic.

Are the duplicate passwords explained by duplicate entries? Let's find out!

Having used a password manager for ten years, I can confidently confirm that the browser extension is not infallible. It is easy to create duplicates. Some examples:
* Registering for a new service saves the sign-up URL (www.example.com/signup, for example). So naturally, the next time I use the service and sign in, I launch the password manager and search for the credentials. But since this URL (www.example.com/login) isn't known to the password manager, I might manually copy the user ID & password, and the browser extension asks if I want to add this pair to the password manager.
* If I change a password, the URL might be different (www.example.com/change-password), and as it is not known to the password manager, it asks if I want to add the new password.
* Not all websites are built with password managers in mind, so the extensions do their best to determine if the fields in the form correspond to user ID and password pairs. On occasion, an input field might look like a password when it isn't.

The problem is that the password manager is intrusive. As a user, I want to perform tasks that require me to sign up for or sign in to a service to update some account details. My goal is to complete a task, be what it may be, and not keep my passwords organized at that particular time. If I see a message asking me if I want to add or update a password, I'll spend a minimal amount of time thinking about what it means and click Yes, Accept, Save, or a variation of it and not risk losing that password to the wind (because having to deal with a password recovery flow is, to me, a terrible experience that involves several steps across devices and services).

I go over the list, one by one, and I confirm my theory:
* https://secure.last.fm/login & https://www.last.fm/settings/lostpassword/confirm
* https://global.irobot.com/manage-your-account/store-reset-password & https://store.irobot.com/default/cart
* https://bookings.copaair.com/CMGS/ItinerarySummary.do & https://www.copaair.com/Sites/cc/es/_layouts/validate.aspx

I see all sorts of services and websites: ieee.org, slack.com, aa.com, live.com, and wired.com. Out of 54 entries in this category, I identified four passwords that are legitimate duplicate passwords that I have now changed and two passwords for accounts that I no longer have access to (I deleted my Dropbox account a few years ago, and I no longer have access to my university's internal apps).
After going over each of the 54 entries with twice-reused passwords, I identified additional ways in which the same password exists multiple times in the password manager:
* Some services allow signing in with an email address, user ID, or account number. We end up with one new entry in the password manager for each.
* Companies acquire other companies and sometimes migrate user accounts—for example, Skype and live.com.
* Companies may have multiple domains for which the credentials are valid.
* Using both the web and mobile apps for the same service.

I found nothing surprising in the five passwords that were reused three times each. The explanation is similar to that for twice-reused passwords.

For n=4, three entries are for accounts for different services. It is a somewhat old password I have not changed in 8 years. There are two pieces of good news here: 1) I have MFA enabled for this account, and 2) the password does not yet show up in HIBP (https://haveibeenpwned.com/).

Finally, for n=5, three of the entries are for the same user/domain, so we're dealing with a password reused on three different services, and none of these are important in any way.

Overall, my password reuse is better than I thought it might be. One area of improvement is to remove duplicate entries to reduce clutter.

### Password length
Passwords of length 12 and 16 represent 66% of the passwords stored in the password manager. This may be due to different defaults in different systems or platforms.

The three longest passwords are 28, 31, and 40 characters long, and the three shortest are 1, 4, and 5 characters long.

I chuckled when I saw what the forty-character password is (for example, if the credential is used to sign in to the planetarium's ticketing system, the password is Tw!nkl3Tw!nkl3L!ttl3St@rHow!Wond3rWh@tYouAr3^17321). As for the 31-character password, it wasn't lyrics to a song but a line from a poem. The 28-character password was randomly generated.

On the other side of the scale, the password with length 1 is just garbage - a password update poorly detected by the password manager's browser extension.

Next on the list is a four-character-long password. It is a PIN for my local library account. I can't do anything about this, as the library's website only supports 4-digit PINs.

The five-character password grants me access to my local and personal development database, so I won't worry about this one.

In general, I do not have concerns about the length of my passwords. Around 90% of the passwords have a length of at least ten, which is enough for now.

### Usernames
Out of 591 entries, there are 107 unique usernames. The majority are, boringly, email addresses. There are a few random word usernames and also a few UUIDs.

A breakdown of email addresses as usernames by provider:
* gmail.com: 13
* fastmail.com: 8
* personal domain: 6
* me.com: 1
* yahoo.com: 1
* outlook.com: 1
* hey.com: 1

The + and . tricks for Gmail and the masked addresses for Fastmail account for the majority of the usernames.

### Defunct services
No service lives forever. Some are acquired, some rebrand, and some shut down.

I skimmed over the list and found a few defunct services:
* hipmunk.com
* okplay.com
* gameschoolonline.com
* venueparking.com
* msots.com
* hackthisbillboard.com
* floydhub.com

I have a question: what happened to the data? Who has it now?

In some cases, the answer is probably buried in an email account.

This analysis would require checking external sources to fully understand the fate of these services and their associated data. It's an important consideration when managing old accounts and their potential security implications.

## Conclusion
After analyzing my password data, I've identified several areas for improvement in my password management practices:
1. Password Reuse: While my password reuse is less extensive than I initially feared, there's still room for improvement. I will address the few instances of legitimate password reuse and clean up duplicate entries to reduce clutter.
2. Password Length: Currently, 91% of my passwords are ten characters or longer, which I find sufficient for now. However, I plan to gradually increase my minimum password length for better security. In the meantime, I'll focus on reviewing and updating the remaining 9%, especially those with very short lengths, where possible.
3. Defunct Services: The presence of defunct services in my password manager is a stark reminder of how online services can suddenly disappear, often with little to no warning. When this happens, users typically have no control over what becomes of their data. This underscores the importance of being cautious about what information I share with online services and considering the potential risks if a service were to abruptly shut down or change ownership.
4. Regular Audits: This analysis has highlighted the importance of regular password audits. I plan to make this a recurring task to maintain good password hygiene.

