# Vision

MonitorMe is a patient monitoring system designed to streamline the process of tracking and analyzing vital signs.

It consolidates data from multiple sources, providing a unified view of a patient's health status.

The system also alerts medical professionals of potential issues based on real-time data analysis. This innovative solution aims to enhance patient care and improve the efficiency of healthcare providers.

## Background
StayHealthy, Inc. is a large and highly successful medical software company located in San Francisco, California, US. They currently have 2 popular cloud-based SAAS products: MonitorThem and MyMedicalData.

MonitorThem a data analytics platform that is used for hospital trend and performance
analytics—alert response times, patient health problem analytics, patient recovery analysis, and so on.

MyMedicalData is a cloud-based patient medical records system used by doctors, nurses, and other health professionals to record and track a patients health records with guaranteed partitioning between patient records.

## Team
We are a team of dedicated architects and specialists, committed to delivering exceptional software and architectural designs. Our collective expertise and passion make us a unique force in the industry.
![us](./img/us.jpeg)

### Sigma Connectivity - Innovating for a Connected Future
At Sigma Connectivity, our mission is to drive innovation and create value through connected solutions and devices. We strive to make our partners stand out in the digital landscape.

With one of Europe's most advanced design, test, and verification labs, we cater to the specific needs of our clients. Our goal is to help bring smart, connected products to market, setting new standards in the tech industry.

### Meet us, meet the Sigma Connectivity Team
We are a group of talented individuals from Sigma Connectivity, specializing in software and architectural design. Our team's strength lies in our ability to innovate and create value through connected solutions and devices.


## Overview
![system overview](./img/overview.png)

# Reqirements analysis
The requirements analysis we have done including functional and non-functional requirements.
Also, after 2 sessions brainstorming, we believe in security and performance is critial to the success.
![brain storming](./img/requirements%20analysis%20brainstorming.png)

## Here are our stories

### The system administrator says:
"I want to be able to enroll new patients into the system, meanwhile.
 I want to be able to allocate/free the system resources, such as bed, sensors.
 I want to be able to assign some healthcare professionals,
 I want to create an instance to pack all things above."

So yes, let's provide an Admin service in the MonitorMe station that includes RoleManager, permissionManager,
let's make resource manager to allocate/release bed, sensors
let's create program to allow the admin to create patient instance so that to register patient, healthcare professionals and resources
here we go!
![System admin works](./img/HighlevelUseCaseAdmin.png)

### The healthcare professional says:
"I want to be able to config threshold for vital sign data, to make the system run data collection service and generate realtime events which are process to generate alert notification to my mobile phone
 I want to be able to quickly identify an abnormal, so I should view real-time vital sign data for the specific patient
 I want create snapshot for the vital data, together write down my notes and upload to MyMedicalData cloud,
 I want to be able to access the patient history stored on the MyMedicalData cloud"

So, let us provide what our healthcare professional needs, vital sign data viewer, realtime monitor services runs on the stations, snapshot creators for generating reports.
Yes, to make his life great!
![Healthcare professional works](./img/HighlevelUsecaseHealthcareProfessionals.png)

### The patient says:
"I want to be able to register on the system so that my mobile phone is able to access all information,
 I want to be able to view my personal helth history so that I can stay informed about my status, also I might go to other hospitals, then my history can be shared with other professionals
 I want to provide my consent for security protocols, especially for my personal data collection and sharing
 I want to be able to request support from healthcare professionals through the system"

 Of course, let's provide a registration service for our patient, and sure we will provide notification services together with it.
 let's provide security service so to let patient to consent on his privacies, and we also provide health data viewer to him.
![Patient is treated well](./img/HighlevelUsecasePatient.png)

### The customer project manager says:
"I want the system to have high performance so that it can handle large amounts of data without slowing down or crashing.
I want the system to be secure so that patient data is protected from unauthorized access.
I want the system to be auto-scalable so that it can be extended for more capacity on site with easy out-of-box setup
I want the system to be highly available so that healthcare professionals can monitor patients at all times, even if some of the sensor devices break, there shall be limited impacts to the system
I want the system is able to automatically scale storage capacity up or down based on the predicted amount of data to be generated
"

Yes, and yes,
let's make a solution for customer project manager. For high performance and scalability consideration, we can implement the MonitorMe system to include 2 parts:
1. MonitorMe station - capable to manage 25 nurse stations, it is able to run most micro services, such as admin services, security services, web servies, it keeps all the data
2. Nurse Station - capable to manage 20 patients, it focus on basic local services, such as physical sensors data collection services, data transmission services, resource manager, and so on

For Security, we should have a dedicated security service runs on MonitorMe station
For Auto-scalability, we can make an nurse station manager service runs on MonitorMe station, this allows the admin of hospital to extend nurse station by themself. We can implement resource manager service runs on nurse station, so this allows the admin of hospital to extend beds by themself.
For high availability, we can implement redundant components and services such as failover clusters, load balancers, and backup systems. we can also implement monitoring tools to detect and alert on potential device broken, if one sensor is broken, the backup sensor still works.

Here we go!
![Customer Project Manager](./img/HighLevelUsecaseCustProjectManager.png)


## Functional requirements
1. Data collection from sensor devices
  MonitorMe should read data from eight different patient-monitoring sensor devices for vital sign input sources: heart rate, oxygen level blood sugar, respiration rate, electrocardiogram (ECG), body temperature, and sleep status (sleep or awake).
1. Data transmition
  All patient sensoring devices communicates within the system regarding vital sign readings at different rates. The system must be able to support the varying data transmission rate in an effective way.
  As data sampling is streaming constantly from many sensor devices, meanwhile, there could be commands interactions to devices for configrations or change settings, the data needs to be queued to keep traffic smooth.
1. Data consolidation
  Just like we create an order for shopping, an entity of 'order' could include various 'shopping items' which are allocated from different product storage. En patient snapshot should include related information such as:
  patient id and patient information
  sensor id and sensor data in a certain time duration
  healscare professionals
1. Data storage
  For each vital sign, it is required that MornitorMe must record and store the past 24 hours of all vital sign readings. A medical professional can review this history, filtering on time range as well as vital sign.
  We believe security is important here, so we consider to make each patients records could be stored in separate database physically separation of data helps to ensure data records are not mixed up. Also, we want further introduce admin functions for access control, data encryption and audit logs to keep detailed logs of all access and changes to patient records.
  A good idea might be we hold most of the data in local MonitorMe, for most 'micro-services', they should be installed and run at local.
  For analysis or research purposes, create anoymized data sets, so to make sure it can't be linked back to individuals.
1. Role and Security Management
  The system should have admin functions for managing roles of patients and healthcare professionals, and for setting data access policies for security profiles.
  For example, when a new patient come to the nurse station, the admin shall be able to enroll the person with devices, healthcare professionals to the system.
1. Micro service platform and services
  Various microservices could be applicable in the MonitorMe system, such as Data collection service, data storage service, data analysis service, user management service, nurse station service, alert notification service, patient report service, api gateway service, security service, and etc.
1. UI/UX
  The UI/UX module of the medical monitoring system should be designed to provide an intuitive and user-friendly interface for healthcare professionals. It should include responsive design, accessibility features, user authentication and authorization, customizable alert settings, effective data visualization tools, optimized performance,  strong security and privacy measures. These technical requirements will ensure that healthcare professionals can effectively monitor patient vital signs and respond quickly to critical situations.


## Non-functional requirements
1. Availability
  The system should be designed to ensure high availability, meaning it should be accessible and usable by medical professionals at all times. This can be achieved through redundant systems, failover mechanisms, and regular maintenance and monitoring.
2. Reliability
  The system must be highly reliable, with minimal downtime or errors. This can be achieved through rigorous testing, quality assurance processes, and regular updates and maintenance.
  For example,
  while one sensor stops working, it should not impact other data collection.
  We should do multi samples for single report, so to make sure each individual measure error does not impact the accuracy, e.g. the Oxygen level is required to report every 5 seconds, but inside of each sensor device, we will implement the measurement of >10 times per seconds, this could even to be configurable by the healthcare professionals.
3. Performance and elasticity
  The system should be designed to handle a large volume of data traffic from users while maintaining fast response times and low latency. This can be achieved through:
   efficient message/data queue,
   architecture design,
   optimized database design,
   and appropriate hardware specifications.
4. Scalability
  The system should be able to scale up or down based on demand, allowing it to accommodate an increasing number of patients and data sources over time.
  This can be achived by structuring between 'nurse station' and 'MonitorMe', to make the flexibility for 'hospitals' or care centers to deploy with light weight or heavy weight.
5. Security
   Given the sensitive nature of the data, the system must ensure high levels of security to protect patient data from unauthorized access or breaches.

## Performance Characteristics

Each patient monitoring device transmits vital sign readings at a different rate:
Heart rate: every 500ms
Blood pressure: every hour
Oxygen level: every 5 seconds
Blood sugar: every 2 minutes Respiration: every second
ECG: every second
Body temperature: every 5 minutes Sleep status: every 2 minutes
Maximum number of patients per physical MonitorMe instance: 500
MonitorMe reads data from eight different patient-monitoring equipment vital sign input sources: heart rate, blood pressure, oxygen level, blood sugar, respiration rate, electrocardiogram (ECG), body temperature, and sleep status (sleep or awake). It then sends the data to a consolidated monitoring screen (per nurses station) with an average response time of 1 second or less. The consolidated monitoring screen displays each patients vital signs, rotating between patients every 5 seconds. There is a maximum of 20 patients per nurses station.

# Business constrains
1. Security and privacy, prioritize data privacy including regulatory compliance, the system must comply with relevant healthcare regulations and standards, such as HIPAA or GDPR, to ensure the privacy and security of patient data.
2. Budget constraints
3. Time to market
4. Maintenance and support, the system must be easy to maintain by both StayHealthy and clients


# Techinical constrains
Some technical constrains could be applicable in the MonitorMe system:
1. Maxium patients per nurse station
2. Maximum patients per MonitorMe instance
3. Data Storage Capacity, for each patients vital sign, Monitor Me must record and store the past 24 hours of all vital sign readings.
4. Security Protocols

# Component Identification
1000 years later...
we have been identifying and adjusting components for 10000 times.

Now we get...

![component identification](./img/components%20identification.png)

# Customer Maintenance, workflows todo
