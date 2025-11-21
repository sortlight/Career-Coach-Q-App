
## Amazon Q Career Coaching App

 #                                      [Skillyzer](https://0mgpa0py.chat.qbusiness.us-west-2.on.aws/#/app/cac7ff71-d18e-4aa2-bd46-1197d5edd733)

### A Skill Gap Analyzer and Training Recommendation System

This project brings together Amazon Q, custom data sources, access controls and automation to create a working career-coaching system. The goal was simple: upload a CV and a job description and it will generate a clear skill gap analysis and further recommend training from both static and dynamic catalogs stored in Amazon S3.


## Table of Contents

1. Project Overview

2. Features

3. Architecture

4. Setup Steps

5. Data Sources

6. Access Control

7. Global Moderation

8. screenshots and Proof of work

9. How to Use the App

10. Verification Status

11. Future Enhancements




###   1. Project Overview

The app functions as an end-to-end skill analysis tool. A learner or coach uploads two things:

*   A CV

*   A job role or job description

The app analyzes the gap and recommends training aligned with the uploaded course catalogs. It supports:

*   Static PDF course catalogs

*   Dynamic S3-hosted catalogs synced daily

*   ACL-based restrictions for sensitive course content

All powered by Amazon Q's workflow, custom input/output cards, S3 integrations and access control.



##   2. Features

**Core Features**

*   Upload CVs and job profiles using Input Cards

*   Skill gap analysis with clear output

*   Training recommendation Output Card

*   Suggested training schedule Output Card

*   Personalized coaching Input Card

**Integrations**

*   Manually uploadeded PDF catalog

*   S3 bucket with training catalogs

*   Daily scheduled sync on the S3 source

**Security & Governance**

*   ACL-based access restrictions

*   Use of existing CareerCoaches group and users

*   Global Controls for restricted keywords


##   3. Architecture

```sql

AWS IAM Identity Center
      |
Amazon Q Business
      |
-------------------------------
|   PDF Data Source           |
|   S3 Data Source            |
-------------------------------
      |
Training Recommendations + Skill Gap Analysis+Training Schedule


```


##   4. Setup Steps

**Step 1. Built the Q Application**

* Created a working app with all required input and output cards.

* Confirmed functionality using test CVs and job description.

* Added training schedule recommendation output card.

* Added personalized coaching input card.

* Verified every card by generating live outputs.

/Screenshots/q_business.png
/Screenshots/app_skillyzer.png


**Step 2. Enhanced the App with Advanced Components** 

* Built and tested the additional components.

* Updated interface to reflect new card flow.



##   5. Data Sources used


 **PDF Data Source**

* Uploaded a static course catalog PDF.

* Synced it successfully as a data source.

/Screenshots/static-pdf-upload.png

**S3 Data Source**

* Created the S3 bucket: course-catalog-career-coach-v1.

* Uploaded at least one training catalog file.

* Added the bucket to Amazon Q as a data source.

* Verified successful sync.

* Configured daily automatic sync.

/Screenshots/bucket_created.png

/Screenshots/s3-objects-uploaded.png

/Screenshots/S3_added_as_data_Source.png 



##   6. Access Control Configuration


**ACL File Applied**

Used the provided ACL JSON:

```json

[
    {
        "keyPrefix": "s3://course-catalog-career-coach-v1/Data/Restricted/Medicine/",
        "aclEntries": [
            {
                "Name": "career.coach.one",
                "Type": "USER",
                "Access": "ALLOW"
            },
            {
                "Name": "career.coach.two",
                "Type": "USER",
                "Access": "DENY"
            }
        ]
    },
    {
        "keyPrefix": "s3://course-catalog-career-coach-v1/Data/Additional-Course-Catalog-A.pdf",
        "aclEntries": [
            {
                "Name": "career.coach.one",
                "Type": "USER",
                "Access": "ALLOW"
            },
            {
                "Name": "career.coach.two",
                "Type": "USER",
                "Access": "ALLOW"
            }
        ]
    },
    {
        "keyPrefix": "s3://course-catalog-career-coach-v1/Data/Additional-Course-Catalog-B.pdf",
        "aclEntries": [
            {
                "Name": "career.coach.one",
                "Type": "USER",
                "Access": "ALLOW"
            },
            {
                "Name": "career.coach.two",
                "Type": "USER",
                "Access": "ALLOW"
            }
        ]
    }
]


```

* Applied the ACL to the S3 data source.

* Tested access using required users:

        *   career.coach.one

        *   career.coach.two

* Confirmed that restricted content is visible only to approved users.


Screenshot Placeholders:

/Screenshots/acl_json_upload.png 

/Screenshots/ACL_Sync.png
/Screenshots/Catalog_access_confirmation.png



##   7. Global Moderation

* Added restricted keywords under Global Controls for example: Gambling, Casino, Kill, Self-harm

* Verified that content containing these terms was blocked.

Screenshot Placeholder:
/Screenshots/blocked_words.png

##   8. Screenshots and Evidence

/Screenshots/app_skillyzer.png 
App interface

/Screenshots/static-pdf-upload.png
PDF sync

/Screenshots/s3-bucket-created.png
S3 bucket

/Screenshots/s3-bucket-synched.png
S3 sync

/Screenshots/Daily_Sync.png
S3 daily schedule

/Screenshots/skill_gap.png
Skill Gap Prompt

/Screenshots/ACL_Sync.png
ACL applied

/Screenshots/Daily_Sync.png
Daily Sync

/Screenshots/last-sync-time.png
Last Sync Time 

/Screenshots/Catalog_access_confirmation.png
Access allowed and denied tests

/Screenshots/blocked_words.png
Blocked Words

/Screenshots/hared_app.png
Shared App

/Screenshots/Verified_App.png 
Verified Q App status



##   9. How to Use the App 

click[Skillyzer](https://0mgpa0py.chat.qbusiness.us-west-2.on.aws/#/app/cac7ff71-d18e-4aa2-bd46-1197d5edd733) to test run app

1.  Upload a CV and job profile.

2.  Review the skill gap analysis generated instantly.

3.  Explore recommended training paths.

4.  Check the suggested learning schedule.

5.  Use personalized coaching input to specify context or user preferences.



##   10. Verification Status

* App shared with the CareerCoaches group.

* Custom labels applied:

            Career Coaching

            AI-powered

* App endorsed and marked as Verified.

/Screenshots/Verified_App_2.png


##   11. Future Enhancements

*   More adaptive, role-based UI behavior

*   Progress tracking panel for learners

*   Real-time training catalog updates

*   Custom coach dashboards


#  Author

Ganiyu Ogundana

AWS Business Intelligence Engineer
