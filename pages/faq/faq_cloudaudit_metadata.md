---
title: CloudCoreo Audit metadata guidelines
tags:
keywords: ""
last_updated: "February 23, 2017"
summary: CloudCoreo Audit metadata guidelines
published: true
sidebar: faq_sidebar
permalink: faq_cloudaudit_metadata.html
folder: faq
toc: false
---

## CloudCoreo Audit metadata guidelines  

There are a number of recommended metadata fields that should be added to an Alert Definition / Rule as part of an Audit Composite. These include Display Name, Description, Details, Suggestion Action, Additional Information, Category, Level, and Link.  

### Category  
Enter a Category name from the list below (or your own category) where you will group Alerts / Rules of the same type together. This is useful for sorting Alerts / Rules in the CloudCoreo WebUI. If you enter a Category that is not from the list below, it may not sort properly in the Plan Results Panel in the CloudCoreo WebUI.  
* Security  
* Scale  
* Dataloss  
* Reliability  
* Availability  
* Performance  
* Visibility  
* Audit  
* Access  
* Policy  
* Cost  

### Level  
Enter a Level from the list below (or your own Level) where you will group Alerts / Rules of the same Level together. This is useful for sorting Alerts / Rules in the CloudCoreo WebUI. If you enter a Level that is not from the list below, it may not sort properly in the Plan Results Panel in the CloudCoreo WebUI. The current recommended Levels are based on syslog error levels ( https://en.wikipedia.org/wiki/Syslog#Severity_level ).  
* Emergency - System is unusable  
* Critical - Critical conditions  
* Error - Error conditions  
* Warning - May indicate that an error will occur if action is not taken.  
* Notice - Events that are unusual, but not error conditions.  
* Informational - Normal operational messages that require no action.  
* Debug - Information useful to developers for debugging the application.  

### Link
The Link field is displayed (and clickable) in the Alert / Rule violation card under “More Info” in the CloudCoreo WebUI. You can add your best practice article or alert violation or other canonical information source to inform the users what the alert is checking for and to help guide the your users who encounter this Alert / Rule violation. It is possible to add the article to the CloudCoreo Knowledge Base via github pull request to the Knowledge Base github repository.

### Display Name
The name that you would like the Alert / Rule to show on the alert violation card.

### Description
The description that you would like the Alert / Rule to show on the alert violation card.

### Details
Any detailed information that you would like the Alert / Rule to show on the alert violation card.

### Suggested Action
Any suggestions for actions that you would like the Alert / Rule to show on the alert violation card.

### Additional information
Any additional information that you would like the Alert / Rule to show on the alert violation card.

