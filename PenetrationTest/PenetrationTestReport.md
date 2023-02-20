# Rekall Corporation

## Penetration Test Report

## AJUHAN CYBERSECURITY, LLC


## Confidentiality Statement

This document contains confidential and privileged information from Rekall Inc. (henceforth known
as Rekall). The information contained in this document is confidential and may constitute inside or
non-public information under international, federal, or state laws. Unauthorized forwarding, printing,
copying, distribution, or use of such information is strictly prohibited and may be unlawful. If you are
not the intended recipient, be aware that any disclosure, copying, or distribution of this document or
its parts is prohibited.


## Table of Contents

- Confidentiality Statement
- Contact Information
- Document History
- Introduction
   - Assessment Objective
- Penetration Testing Methodology
   - Reconnaissance
   - Identification of Vulnerabilities and Services
   - Vulnerability Exploitation
   - Reporting
- Scope
- Executive Summary of Findings
   - Grading Methodology
   - Summary of Strengths
   - Summary of Weaknesses
- Executive Summary Narrative
- Summary Vulnerability Overview
- Vulnerability Findings


## Contact Information

**Company Name:** AJUHAN CYBERSECURITY, LLC

**Contact Name:** Alexander Juhan

**Contact Title:** Penetration Tester

## Document History

Version | Date | Author(s) | Comments
---|---|---|---|
001 | 02/10/2023 | Alexander Juhan | 


## Introduction

In accordance with Rekall policies, our organization conducts external and internal penetration tests
of its networks and systems throughout the year. The purpose of this engagement was to assess the
networks’ and systems’ security and identify potential security flaws by utilizing industry-accepted
testing methodology and best practices.

For the testing, we focused on the following:

```
● Attempting to determine what system-level vulnerabilities could be discovered and exploited
with no prior knowledge of the environment or notification to administrators.
● Attempting to exploit vulnerabilities found and access confidential information that may be
stored on systems.
● Documenting and reporting on all findings.
```
All tests took into consideration the actual business processes implemented by the systems and
their potential threats; therefore, the results of this assessment reflect a realistic picture of the actual
exposure levels to online hackers. This document contains the results of that assessment.

### Assessment Objective

The primary goal of this assessment was to provide an analysis of security flaws present in Rekall’s
web applications, networks, and systems. This assessment was conducted to identify exploitable
vulnerabilities and provide actionable recommendations on how to remediate the vulnerabilities to
provide a greater level of security for the environment.

We used our proven vulnerability testing methodology to assess all relevant web applications,
networks, and systems in scope.

Rekall has outlined the following objectives:


## Objective

Find and exfiltrate any sensitive information within the domain.

Escalate privileges.

Compromise several machines.


## Penetration Testing Methodology

### Reconnaissance

We begin assessments by checking for any passive (open source) data that may assist the
assessors with their tasks. If internal, the assessment team will perform active recon using tools
such as Nmap and Bloodhound.

### Identification of Vulnerabilities and Services

We use custom, private, and public tools such as Metasploit, hashcat, and Nmap to gain perspective
of the network security from a hacker’s point of view. These methods provide Rekall with an
understanding of the risks that threaten its information, and also the strengths and weaknesses of
the current controls protecting those systems. The results were achieved by mapping the network
architecture, identifying hosts and services, enumerating network and system-level vulnerabilities,
attempting to discover unexpected hosts within the environment, and eliminating false positives that
might have arisen from scanning.

### Vulnerability Exploitation

Our normal process is to both manually test each identified vulnerability and use automated tools to
exploit these issues. Exploitation of a vulnerability is defined as any action we perform that gives us
unauthorized access to the system or the sensitive data.

### Reporting

Once exploitation is completed and the assessors have completed their objectives, or have done
everything possible within the allotted time, the assessment team writes the report, which is the final
deliverable to the customer.


## Scope

Prior to any assessment activities, Rekall and the assessment team will identify targeted systems
with a defined range or list of network IP addresses. The assessment team will work directly with the
Rekall POC to determine which network ranges are in-scope for the scheduled assessment.

It is Rekall’s responsibility to ensure that IP addresses identified as in-scope are actually controlled
by Rekall and are hosted in Rekall-owned facilities (i.e., are not hosted by an external organization).
In-scope and excluded IP addresses and ranges are listed below.


## Executive Summary of Findings

### Grading Methodology

Each finding was classified according to its severity, reflecting the risk each such vulnerability may
pose to the business processes implemented by the application, based on the following criteria:

**Critical**: Immediate threat to key business processes.

**High**: Indirect threat to key business processes/threatto secondary business processes.

**Medium**: Indirect or partial threat to business processes.

**Low**: No direct threat exists; vulnerability maybe leveraged with other vulnerabilities.

**Informational**: No threat; however, it is data thatmay be used in a future attack.

As the following grid shows, each threat is assessed in terms of both its potential impact on the
business and the likelihood of exploitation:

![Exploitation Likelihood](https://user-images.githubusercontent.com/113793122/219986277-f67fdc9b-5a5b-477e-992b-ba7d3ce6ddf7.png)


### Summary of Strengths

While the assessment team was successful in finding several vulnerabilities, the team also
recognized several strengths within Rekall’s environment. These positives highlight the effective
countermeasures and defenses that successfully prevented, detected, or denied an attack technique
or tactic from occurring.

```
● Use of offensive tools like Metasploit and Nmap to analyze defenses
● Proactive approach to security through the use of penetration testing
● Limited number of vulnerable hosts to exploit.
```
### Summary of Weaknesses

We successfully found several critical vulnerabilities that should be immediately addressed in order
to prevent an adversary from compromising the network. These findings are not specific to a
software version but are more general and systemic vulnerabilities.

```
● Rekall’s website is vulnerable to code injection.
● Our test uncovered a number of back-end vulnerabilities such as directory traversal.
● The Linux server contains a variety of weaknesses to exploit such as poor password security.
● There is a plethora of publicly accessible information that is extremely sensitive, such as a GitHub repository that contains usernames and passwords.
● The Windows server utilizes insecure applications such as SLMail.
```

## Executive Summary Narrative

```
● Rekall’s website contains multiple text input fields that are vulnerable to code injection. For
example, in the section that allows comments to be left, our team was able to inject a script
that produced this message: 
```
![Day1_Flag3](https://user-images.githubusercontent.com/113793122/219986175-9746bc73-fc9a-40ec-89f6-5c982a586b63.png)

```
● The website also allows files to be uploaded, which creates an opportunity for malicious
users to inject scripts directly to the website.
```
```
● By utilizing the inspect tool on the login page, our team discovered a username and
password that allowed us to login to the website:
```
![image (2)](https://user-images.githubusercontent.com/113793122/219986324-653e9cfa-a10d-4393-889e-e8fec16251e9.png)
```
● By pinging totalrekall.xyz, our team was able to find the ip address of the Linux server:
```
![Night 2 Flag 2](https://user-images.githubusercontent.com/113793122/219986488-a4ff5e6d-d9fa-4d87-8914-d165117284c1.png)
```
● A domain lookup of the server provided a lot of exploitable information, such as the
username of the sysadmin:
```
![Screenshot_20230206_064748](https://user-images.githubusercontent.com/113793122/219986510-4211fb77-b17f-4e9d-931f-6c77c3104402.png)

```
● With this information, our team was able to SSH (remote login) to the Linux server using the
username: alice. Our team guessed a number of basic passwords to attempt to login using
this username and was successful with the use of password: alice. This is an extremely
insecure password and username combination, with critical levels of vulnerability to the
server. If a malicious user were to login with this information, they would have unrestricted
levels of access to the Linux server.
```
![image (12)](https://user-images.githubusercontent.com/113793122/219986574-e57c99c7-1982-421d-906f-355fbb267588.png)

```
● An nmap scan of the Linux server provided our team with all of the host addresses:
```
![host list](https://user-images.githubusercontent.com/113793122/219986597-2ca2f64b-8aa9-4e9b-81f8-80dba072732a.png)

```
● Rekall has a GitHub repository that contains sensitive information, including a username and
password that our team used to exploit the windows server:
```
![image (13)](https://user-images.githubusercontent.com/113793122/219986612-aa903eb4-4ed4-44a0-a10c-9dcf733d8bfa.png)

```
● The Windows server utilizes an insecure application called Seattle Lab Mail, or SLMail.
Using an offensive tool called Metasploit, our team was able to use this application as an
entry point to login to the Windows server:
```
![image (14)](https://user-images.githubusercontent.com/113793122/219986640-851f7d29-75c8-41b8-86ad-252e8c344e38.png)

```
● Using this entry point through the SLMail exploit, our team was able to go further and use
what is known as a hash dump, which essentially displays all of the server’s usernames and
passwords:
```
![image (16)](https://user-images.githubusercontent.com/113793122/219986655-49dc4f9c-8f94-445e-8d97-7523738dd6fb.png)

```
● The Windows server is also vulnerable to FTP (File Transfer Protocol) exploits. Using
Anonymous Authentication, a popular tool used by hackers, our team was able to gain
access to the Windows server, along with sensitive documents:
```
![Night 3 Flag 3](https://user-images.githubusercontent.com/113793122/219986679-288db9ab-5e6a-4a41-b7ca-88315faf7aec.png)


## Summary Vulnerability Overview


Vulnerability Severity
```
Rekall’s website is vulnerable to code injection. Critical
```
```
Our test uncovered a number of back-end vulnerabilities such as directory
traversal. Critical
```
```
The Linux server contains a variety of weaknesses to exploit such as poor
password security. Critical
```
```
There is a plethora of publicly accessible information that is extremely
sensitive, such as a GitHub repository that contains usernames and
passwords. Critical
```
```
The Windows server utilizes insecure applications such as SLMail. Critical
```

The following summary tables represent an overview of the assessment findings for this penetration test:



## Hosts and Ports 

| Scan Type    | Total                                                                                                                                 | 
|--------------|-----------                                                                                                                            |
| Hosts        | 192.168.14.35, 172.22.117.20, 172.22.117.100, 192.168.13.1, 192.168.13.10, 192.168.13.11, 192.168.13.12, 192.168.13.13, 192.168.13.14 |
| Ports        | 110, 4444, 55454                                                                                                                      | 

## Risk and Severity Level 

| Exploitation Risk | Total |                                                                                                                               
|-------------------|-------|                                                                                                                           
| Critical          |   5   |
| High              |       |
| Medium            |       |
| Low               |       |

## Vulnerability Findings


Vulnerability 1 Findings
```
Rekall’s website is vulnerable to code injection.
```
```
Type: Web app 
```
```
Risk Rating: Critical
```
```
Description: Rekall’s website contains multiple fields that allow text input. Our penetration
test exploited these fields by injecting code that displayed sensitive company
data.
```
```
Affected Hosts: 192.168.14.35
```
```
Remediation: Implement input validation to remove this vulnerability. Ensure that only
allowed inputs are accepted. One of the text fields had this employed, however
our team circumvented it by changing “script” to “scSCRIPTript,” which avoided
the detection of the second instance of the word script hidden inside the first.
```

Vulnerability 2 Findings
```
Our test uncovered a number of back-end vulnerabilities such as directory
traversal.
```
```
Type: Linux OS
```
```
Risk Rating: Critical
```
```
Description: The Linux server was found at totallrekall.xyz. Utilizing directory traversal, our
team was able to navigate through various directories by adding various
endings to the site address such as totallrekall.xyz/index.php/admin/.
```
```
Affected Hosts: 192.168.13.1, 192.168.13.10, 192.168.13.11, 192.168.13.12, 192.168.13.13,
192.168.13.14
```
```
Remediation: The remediation for this exploit is to validate the user input before processing
it, similarly to the code injection exploit. After validating the input, the server
should canonicalize the path (or implement the most direct pathway) to prevent
a malicious user from deviating from the set pathway.
```

Vulnerability 3 Findings
```
The Linux server contains a variety of weaknesses to exploit such as poor
password security.
```
```
Type: Linux OS
```
```
Risk Rating: Critical
```
```
Description: Our team was able to SSH (remote login) to the Linux server using the
username: alice, which was found when we performed a domain lookup on
totalrekall.xyz. Our team guessed a number of basic passwords to attempt to
login using this username and was successful with the use of password: alice.
This is an extremely insecure password and username combination, with
critical levels of vulnerability to the server. If a malicious user were to login with
this information, they would have unrestricted levels of access to the Linux
server.
```
```
Affected Hosts: 192.168.13.1, 192.168.13.10, 192.168.13.1192.168.13.141, 192.168.13.12, 192.168.13.13, 192.168.13.14
```
```
Remediation: Implement a stronger password policy. At the absolute minimum, passwords
should contain a mix of alphanumeric characters, requiring a special character
(such as !, ?, or +), and avoiding using common phrases, especially names.
Additionally, requiring users to change their passwords more frequently can
reduce the threat that this risk provides.
```

Vulnerability 4 Findings
```
There is a plethora of publicly accessible information that is extremely
sensitive, such as a GitHub repository that contains usernames and
passwords.
```
```
Type: (Web app/Linux OS/Windows OS)
```
```
Risk Rating: Critical
```
```
Description: Rekall has allowed data that risks the company’s security to be publicly
accessible online. For example, Rekall has a GitHub repository that contains
sensitive information, including a username and password that our team used
to exploit the windows server. Additionally, a domain lookup of the server
provided a lot of exploitable information, such as the username of the
sysadmin.
```
```
Affected Hosts: 192.168.14.35, 172.22.117.20, 172.22.117.100, 192.168.13.1, 192.168.13.10,
192.168.13.11, 192.168.13.12, 192.168.13.13, 192.168.13.14
```
```
Remediation: Ensure that employees are being trained regularly in proper data
management. Using the results of this pentest, Rekall should remove all of the
data that was discovered from online.
```

Vulnerability 5 Findings
```
The Windows server utilizes insecure applications such as SLMail.
```
```
Windows OS
```
```
Risk Rating: Critical
```
```
Description: The Windows server utilizes an insecure application called Seattle Lab Mail, or
SLMail. Using an offensive tool called Metasploit, our team was able to use
this application as an entry point to login to the Windows server. Using this
entry point through the SLMail exploit, our team was able to go further and use
what is known as a hash dump, which essentially displays all of the server’s
usernames and passwords. The Windows server is also vulnerable to FTP
(File Transfer Protocol) exploits. Using Anonymous Authentication, a popular
tool used by hackers, our team was able to gain access to the Windows
server, along with sensitive documents.
```
```
Affected Hosts: 172.22.117.20, 172.22.117.100
```
```
Remediation: Monitoring log files and remaining on the lookout for these exploits is the best
mitigation strategy.
```

