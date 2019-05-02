---
title: Flutter app
date: 2017-03-26
publishdate: 2017-03-26
---
# Software Design Document
## Jack of All Trades
Author: Pownthep Laokhunthot
Reviewer: Pownthep Laokhunthot
Created date: 24 of April 2019

## Overview
A mobile application that will allow employer to post jobs and find workers around local areas on demand. The application will also provide contact details to the worker and as well as direction to get to the work site as specified by the employer. 

## Context
Young people in modern society often find themselves with nothing to do outside of studying and going out with friends. When they are at home, they mostly spent it either playing video games, browsing the internet or watching television. I believe that young people should be able find work experience outside of school. Of course, they can always look for a part time job, but that requires time commitment and a student's schedule may not be so flexible to accomodate such commitment. I believe this app will allow people to earn a  money and work experience on the side, while having the flexibility to do other things. 

## Goals and Non-Goals
- Employer will be able to easily find people around local areas to help do errands.
- Worker (students or freelancer) will be able to make small income on the side on their free time.

## Milestones (Daily update so will be subjected to change)
### Start Date: 24 of April 2019
- Milestone 1 - Mock up user interface: 25 of April 2019
- Milestone 2 - Scaffold user interface: 26 of April 2019
- Milestone 3 - Implement user registration 27 of April 2019
- Milestone 4 - Implement user authentication 28 of April 2019
- Milestone 5 - Implement job posting 29 of April 2019
- Milestone 6 - Implement job search 30 of April 2019
- Milestone 7 - Implement job application 1 of May 2019

End Date: 24 of May 2019

## Existing Solution
Handyman App (https://play.google.com/store/apps/details?id=com.algosoft.handyman&hl=en)
This is a platform for connecting individuals looking for household services with service professionals.
This application is similar in that it allows handyman businesses to advertise their services on the app.


LINE MAN (https://play.google.com/store/apps/details?id=com.linecorp.linemanth&hl=th) 
### This application provides five main services:
- On demand food delivery
- On demand transport
- On demand package delivery
- On demand messenger
- On demand grocery shopping
- Fast response time.

Grab (https://play.google.com/store/apps/details?id=com.grabtaxi.passenger&hl=en)
- This application is similar to LINE MAN but offers it at a much cheaper price. The delivery fee can go as low as 10 Baht. Their services include:
- On demand food delivery
- On demand transport
- On demand package delivery
- On demand messenger
- On demand grocery shopping
- Fast response time

Indeed Job Search (https://play.google.com/store/apps/details?id=com.indeed.android.jobsearch&hl=en)
### Indeed provide the following services:
- Employers can:
- Post job
- Respond to job applicants

### Job applicant can:
- Upload a resume/cv
- Submit job application
- Track job status

## Proposed Solution
A platform that allows employers and employee to connect and negotiate directly. 

### The before job process is as follows:
- An employer post a job specifying the category, the requirements or qualification, the pay, the estimated workhour, the location, the date and time and the search area. 
- A job that is posted will be updated to every user in realtime.
- Job applicant can apply for any job.
- Job applicant can choose to cancel their applicant at anytime if their applicant has not accepted or refused. 
- After an applicant for a job, the employer of that job will receive realtime notification that someone has apply and can choose accept, refuse, or wait for more applicants to arrive. 
- Employer can choose to chat directly with the applicant directly within the app.
- Once an applicant has been chosen by the employer all the other pending applicant will be refused and notifications will be sent to all unsuccessful applicants in realtime.
- After an applicant was chosen by the employer, the applicant will be ask to accept the job again as confirmation.
- *Extra feature - change job status to doing

### During job process:
- User at this stage will have access to realtime location tracking and direction to the job site as specified by the employer.

### After job process:
- User will be to review their employer and employee. The review score of each user which will be publicly visable to other users. 
- *Extra feature - change job status to doing

### Technical implementation will require:
- Database with realtime update capabilities
- Mobile SDK that provides basic UI components and access to Geolocation API

### Core features
- Authentication
- Job search
- Job posting
- Job application
- Realtime chat
- Realtime location tracking

## Alternative Solutions

## Testability, Monitoring and Alerting

## Cross-Team Impact

## Open Questions
- How does the application stop user who are under age from accessing the application?
- Will the platform be liable for any damage that may occur while using the application or while conducting the job?
- What is the user registration process?

## Detailed Scoping and Timeline
Timeline: 24 of April until 24 of May 2019
Scope: Implement core features as listed in proposed solution section.
