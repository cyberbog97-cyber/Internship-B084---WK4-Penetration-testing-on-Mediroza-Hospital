# PENETRATION TESTING REPORT 
**Mediroza General Hospital – Week 4 Practical**

**Prepared by**: Olusoji Samuel

**Target Website**: https://medirozahospital.com 

**Date**: 26 November 2026 

**Client:** Medizora Hospital

**Assessment** Type: Black-Box Penetration Testing 

**Duration:** 5 Days 

**LIABILITY DISCLAIMER**

This report documents the activities and findings from an authorised penetration testing exercise conducted as part of an educational practical. 

The assessment was carried out within the scope and permission provided for the exercise. The techniques and tools used were intended to identify security weaknesses and demonstrate their potential impact on the target website. 

The information contained in this report is intended for educational and security assessment purposes only. Any sensitive information obtained during the exercise should be handled confidentially and should not be shared with unauthorised individuals. 

The findings and recommendations are based on the activities performed during the assessment. They should not be interpreted as a guarantee that every security weakness within the organisation's infrastructure has been identified. 

 

**1. EXECUTIVE SUMMARY**

This report presents the results of a black-box penetration testing exercise conducted against the Mediroza General Hospital website. 

The main objective was to examine the website's security, identify possible entry points, test its authentication process and determine whether sensitive information could be accessed without proper authorisation. 

Several tools were used during the assessment, including Dirsearch, SQLmap, an Online PDF Hash Extractor and NetworkWalks Password Cracker. 

During the exercise, I successfully gained access to the patient portal by exploiting an SQL injection weakness in the login form. This allowed me to retrieve three patient laboratory report PDFs. 

I also examined the website's exposed directories using Dirsearch. During this process, I discovered an old patch in the scan results. Further investigation of the discovered resource led me to staff salary information and shareholder details. 

The three retrieved PDF files were also examined during the second milestone. Their password hashes were extracted and submitted for password recovery, allowing me to recover their contents. 

Overall, the practical demonstrated weaknesses involving authentication, access restrictions and the exposure of sensitive information. These findings could have serious consequences if similar weaknesses existed on a live system without appropriate security controls. 

 

 
 
**2. SCOPE AND METHODOLOGY**
**2.1 Scope of Assessment**
The assessment was conducted against the following target: 

**Organisation:** Mediroza General Hospital    
**Website:** https://medirozahospital.com
**Assessment Type**: Black-box penetration testing   
**Duration:** Five days 

* The practical covered three main milestones: 
* Gaining initial access to the patient portal and retrieving three patient laboratory reports. 
* Extracting and recovering the passwords protecting the retrieved PDF files. 
* Investigating the website for staff salary information and shareholder details. 

The assessment followed the authorised scope provided for the practical. Testing was limited to the specified target and did not involve social engineering or denial-of-service activities. 

**2.2 Tools Used** 
 
The following tools and resources were used during the assessment: 

**Tool** 
* Kali Linux
Purpose:Operating system used for security testing 
* Dirsearch 
Purpose:Directory and file enumeration 
* SQLmap 
Purpose:SQL injection testing 
* Web Browser 
Purpose:Accessing and examining the website 
* Online PDF Hash Extractor 
Purpose:Extracting password hashes from PDF files 
* NetworkWalks Password Cracker 
Purpose:Attempting to recover PDF passwords 

**2.3 Methodology**

The assessment followed a practical, milestone-based approach. 

I began by examining the target website and searching for accessible directories and files. I then investigated the patient portal's login mechanism and tested how it handled user input. 

After gaining access to the portal, I retrieved the three PDF laboratory reports required for the exercise. I proceeded to examine their protection mechanisms, extract their password hashes and attempt password recovery. 

For the final milestone, I continued directory enumeration and investigated an old patch identified in the Dirsearch results. This provided a lead that helped me locate the requested staff salary and shareholder information. 
 

**3. FINDINGS AND PROOF OF EXPLOITATION**

**3.1 Milestone 1 – Initial Access and Patient Portal**

The first milestone focused on identifying possible entry points on the website and gaining access to the patient portal. 
I started by examining the target website and checking its login functionality. During this process, I tested how the application handled the information entered into the login form. 
I discovered that the patient portal was vulnerable to SQL injection. By entering the following input into the login form: 

**admin'--**
 
I was able to bypass the normal authentication process and gain access to the patient portal. 
After successfully accessing the portal, I located and retrieved the three patient laboratory report PDFs required for the practical. 
Result: Successful access to the patient portal and retrieval of three patient laboratory report PDFs. 

Potential Impact: 
* Unauthorised access to confidential patient records. 

* Exposure of sensitive medical information. 

* Possible violation of patient privacy and confidentiality. 

* Potential misuse of information obtained from the portal. 

Risk Rating: Critical 

Recommendation: 

The hospital should review and correct the authentication mechanism. All database queries should use parameterised statements to prevent user input from changing the structure of database queries. Authentication controls and database permissions should also be reviewed to prevent unauthorised access. 

Evidence: Screenshot of the login test, successful portal access and the three retrieved PDF reports. 

**3.2 SQLmap Testing**

I also used SQLmap to examine the target for possible SQL injection weaknesses. 

During the test, SQLmap reported that the website appeared to have a Web Application Firewall (WAF) or Intrusion Prevention System (IPS). The tool did not identify a testable parameter in the supplied target and returned an HTTP 403 Forbidden response. 

Although SQLmap did not independently confirm an injection during this particular scan, the manual login test described in Section 3.1 successfully demonstrated the authentication bypass. 

It is important to distinguish the two results: the manual test was successful, while the SQLmap scan did not confirm the vulnerability. 

Evidence: 
 
 

**3.3 Milestone 2 – PDF Hash Extraction and Password Recovery** 

The second milestone focused on examining the three PDF reports retrieved from the patient portal. 

I used an Online PDF Hash Extractor to obtain the password hashes associated with the PDF files. The extracted hashes were then submitted to NetworkWalks Password Cracker for password recovery. 

The purpose of this process was to determine whether the protection applied to the documents could be bypassed through password recovery. 

I successfully recovered the contents of all three PDF files, completing the second milestone. 

**Result:** Password recovery was successful for all three PDF reports, and their contents were accessible. 

Potential Impact: 

* Confidential patient documents could be accessed by individuals who obtain the files. 

* Weak document passwords may not provide sufficient protection for sensitive records. 

* Exposure of medical information could create privacy and data protection concerns. 

**Risk Rating**: High 

**Recommendation:**

The hospital should avoid relying on weak or easily recoverable PDF passwords as its main method of protecting sensitive documents. Strong, unique passwords and appropriate encryption should be used. Access to patient reports should be controlled through secure authentication and authorisation mechanisms. 
 

**3.4 Milestone****3–Directory Enumeration and Discovery of Staff Salaries and Shareholder Information**

For the third milestone, I used Dirsearch to continue examining the website for exposed directories and files. 

During the scan, I discovered several paths and resources, including an old patch that appeared in the Dirsearch results. I investigated the discovered resource and followed the information it revealed. 

This eventually allowed me to locate the hospital's staff salary details and shareholder information, completing the third milestone. 

The discovery showed how outdated files or patches left accessible on a web server can create opportunities for unauthorised access to information that should remain confidential. 

**Potential Impact:**
* Exposure of confidential employee salary information. 
* Unauthorised access to shareholder details. 
* Possible misuse of internal organisational information. 
* Privacy and confidentiality risks for the hospital. 
* Reputational damage if the information were exposed publicly. 

**Risk Rating:** High 

**Recommendation**: 

The hospital should review its web server for outdated patches, backup files and unused resources. Files that are no longer required should be removed, while necessary resources should be protected with appropriate access controls. 

Regular directory reviews should also be conducted to identify exposed files and prevent sensitive information from being accessed by unauthorised users. 



**3.5 Other Directory Enumeration Observations**

Dirsearch also identified a number of additional paths on the target website, including: 

*/about.html 
*/staff/ 
*/robots.txt 
*/wp-admin/ 
*/server-status 
*/controlpanel/ 
*/webmail/ 
*/wp-login.php 

The scan returned different HTTP response codes, including 200, 301 and 403. 

These responses indicated that some paths were accessible, some redirected to other locations and others restricted access. 

However, the presence of a directory or a particular HTTP response code does not automatically mean that the resource contains a vulnerability. Further examination is needed to establish the security impact of each path. 

**4. RISK RATING** 

The following table summarises the main findings from the assessment and their potential impact. 

Finding,Risk Level,Reason 

* SQL injection authentication bypass 
Risk rating: Critical 
Reason: Allowed access to the patient portal without normal authentication 

* Exposure of patient laboratory reports 
Risk rating: Critical 
Reason: Confidential medical documents were retrieved 

* PDF password recovery 
Risk rating: High 
Reason: Password protection on the retrieved documents was overcome 

* Exposure of staff salaries and shareholder information 
Risk rating: High 
Reason: Sensitive organisational information was located through the old patch discovered using Dirsearch 

* Exposed directories and outdated resources 
Risk rating: Medium 
Reason: Could provide information or entry points for further investigation 

* WAF/IPS detection during SQLmap testing 
Risk rating: Informational 
Reason: Indicates a security control was detected, but does not establish its effectiveness 

The risk ratings reflect the potential impact of the findings demonstrated during the practical. The most serious issues were the authentication bypass and the exposure of confidential patient information. 
 
 
 
 
 
 
 
**5. RECOMMENDATIONS AND REMEDIATION**

Based on the findings from the assessment, the following actions are recommended: 
 
**5.1 Fix the SQL Injection Weakness**

The hospital should review the patient's portal's login functionality and ensure that all database queries use parameterized statements. User input should never be directly incorporated into SQL queries. 
 
**5.2 Improve Patient Portal Access Controls**

Access to patient records should require proper authentication and authorisation. The hospital should also review existing user permissions to ensure that individuals can only access information relevant to their roles. 

**5.3 Strengthen PDF Document Protection**

Sensitive PDF documents should be protected using strong encryption and secure password practices. However, document encryption should be supported by proper access controls rather than used as the only security measure. 

**5.4 Remove or Restrict Outdated Files**

The old patch discovered during directory enumeration should be reviewed. Outdated patches, unused files, and unnecessary backups should be removed or restricted to prevent unauthorized access. 

**5.5 Protect Confidential Organizational Information**

Staff salaries, shareholder details and other internal records should not be stored in publicly accessible directories. Appropriate authentication and authorization controls should be applied to all sensitive resources. 
 
**5.6 Conduct Regular Security Assessments**

The organization should carry out regular security reviews of its website and web server. These assessments should include directory enumeration, authentication testing, configuration reviews, and checks for exposed files. 

 

 
**6. CONCLUSION**

The Week 4 penetration testing exercise provided an opportunity to examine the security of the Mediroza General Hospital website and demonstrate how weaknesses in web applications can lead to the exposure of confidential information. 

During the assessment, I successfully bypassed the patient portal's login mechanism through SQL injection and retrieved three patient laboratory report PDFs. I then extracted their password hashes and recovered the contents of all three documents. 

Using Dirsearch, I also discovered an old patch among the website's exposed resources. Further investigation led to the discovery of staff salary information and shareholder details. 

The exercise demonstrated the importance of secure authentication, proper file management, strong document protection and effective access controls. It also showed how outdated resources left on a web server can create additional security risks. 

The findings highlight areas that require attention, particularly the protection of patient records and internal organisational information. Implementing the recommended security measures would help reduce these risks and improve the overall security of the hospital's web infrastructure. 

 
 
 
 

**7. EVIDENCE COLLECTED**

The following evidence should be included in the final submission: 
* Dirsearch scan results showing discovered directories and files. 
<img width="1920" height="1080" alt="Screenshot 2026-11-26 015147" src="https://github.com/user-attachments/assets/4d8a1c1c-2098-44ee-ae26-741f6993c300" />
<img width="1920" height="1080" alt="Screenshot 2026-11-26 015204" src="https://github.com/user-attachments/assets/e37a9bf1-8946-4ac7-887c-cfac34e5f9c4" />
* Screenshot of the patient portal login test
<img width="1920" height="1080" alt="Screenshot 2026-11-26 031812" src="https://github.com/user-attachments/assets/4e98cfc3-e702-41ab-bee2-a347a67e0f11" />
* Screenshot demonstrating successful access to the patient portal. 
<img width="1920" height="1077" alt="Screenshot 2026-11-25 202511" src="https://github.com/user-attachments/assets/39d4cf18-9507-44fe-8db1-9b6915c6a180" />
* SQLmap output showing the WAF/IPS detection and HTTP 403 response. 
<img width="1920" height="1080" alt="Screenshot 2026-11-26 015556" src="https://github.com/user-attachments/assets/553ca0cd-b17a-417d-a634-c14e41f48dda" />
* Screenshot of the Online PDF Hash Extractor results. 
<img width="1920" height="1080" alt="Screenshot 2026-11-26 032036" src="https://github.com/user-attachments/assets/a680e07d-f695-4eb8-85a3-21ce80a5e756" />
<img width="1920" height="1075" alt="Screenshot 2026-11-26 032022" src="https://github.com/user-attachments/assets/9988b2ab-280c-49f8-a479-c3bed74258e5" />
<img width="1920" height="1067" alt="Screenshot 2026-11-26 032051" src="https://github.com/user-attachments/assets/b2f868a8-67fb-45a1-b43b-cd2040c9b45b" />
* Screenshot of NetworkWalks Password Cracker results.
<img width="1920" height="1063" alt="Screenshot 2026-11-26 010506" src="https://github.com/user-attachments/assets/b2f12dcd-3033-43df-a72f-97864da43443" />
<img width="1920" height="1080" alt="Screenshot 2026-11-26 011423" src="https://github.com/user-attachments/assets/6f75cbd9-25e8-48fd-a646-9621f7e1693d" />
<img width="1920" height="1080" alt="Screenshot 2026-11-26 010553" src="https://github.com/user-attachments/assets/3318e459-bb55-4741-9d1c-6319b8b3654f" />


**Confidentiality Note**: Any screenshots or report attachments containing patient names, identification numbers, dates of birth, medical results, staff salary details or shareholder information should be redacted before general circulation. Original evidence should be retained and submitted only through the authorised, secure channel required for the practical. 
END OF REPORT 

 
