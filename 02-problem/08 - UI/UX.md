# UI/UX
various problem regarding UI/UX has been addressed, for example:

### Information overload:
Too much data can be overwhelming for healthcare professionals, making it difficult to focus on critical information. A well-designed UI can help prioritize and organize data to make it easier to consume.

### Alert fatigue:
Healthcare professionals may receive too many alerts, leading to desensitization and missed critical alerts. An effective UI can help differentiate between critical and non-critical alerts and provide customizable alert settings.

### User error:
Poorly designed interfaces can lead to user errors, such as misinterpreting data or entering incorrect values. A well-designed UI can minimize the risk of user errors by providing clear instructions and intuitive controls.

### Lack of customization:
Different healthcare professionals may have different preferences and needs when it comes to monitoring patients. A customizable UI can allow users to tailor the interface to their specific needs.

### Inadequate data visualization:
Poor data visualization can make it difficult to understand trends and patterns in patient data. Effective data visualization techniques, such as charts and graphs, can help healthcare professionals quickly identify changes in patient status.

### Slow response time:
A slow UI can lead to delays in responding to critical situations. Optimizing the UI for speed and performance can help ensure rapid response times.

### Inadequate security:
A poorly designed UI can compromise patient privacy and security. Strong authentication and authorization mechanisms, as well as data encryption, can help protect sensitive patient data.

### Limited mobility:
Healthcare professionals may need to access patient data from different locations and devices. A responsive UI design can ensure that the interface works seamlessly across different devices and screen sizes.

### Poor user feedback:
Healthcare professionals may not always know if they have successfully completed an action or submitted data. Clear user feedback, such as confirmation messages and progress indicators, can help ensure that users know what is happening.

## requirements
The system should send the data to a consolidated monitoring screen (per nurses station) with an average response time of 1 second or less.

The consolidated monitoring screen should display each patient's vital signs, rotating between patients every 5 seconds.

Medical professionals should receive alert push notifications of a potential problem based on raw data analysis to a StayHeathy mobile app on their smart phone as well as the consolidated monitoring screen in each nurses station.

A medical professional should be able to review this history, filtering on time range as well as vital sign.

Each patient monitoring device should transmit vital sign readings at a different rate: Heart rate: every 500ms, Blood pressure: every hour, Oxygen level: every 5 seconds, Blood sugar: every 2 minutes, Respiration: every second, ECG: every second, Body temperature: every 5 minutes, Sleep status: every 2 minutes.

The system should be able to send alert push notifications to a StayHeathy mobile app on a medical professional's smart phone.

## todo
admin function

there shall be dashbords

configuration to choose which data/patients to display
