# Data Collection from Sensor Devices

## Section Overview
This document addresses the software design considerations for collecting data from various sensor devices in the MonitorMe system. It outlines problems and proposes solutions to ensure efficient data collection.

The system should read data from eight different patient-monitoring equipment vital sign input sources: heart rate, blood pressure, oxygen level, blood sugar, respiration rate, electrocardiogram (ECG), body temperature, and sleep status (sleep or awake).

If any of vital sign device (or software) fails, the system must still function for other vital sign monitoring (monitor, record, analyze, and alert).
The system should be able to function even if one of the vital sign devices fails.

# Problems and Solutions


## 1. Data Synchronization

###  1.1 Design Solution:
    Centralized data synchronization system where data from all sensors are timestamped upon reception and stored in a queue. A dedicated thread continuously processes the queue, ensuring that data is processed in the order it was received.

###  1.2 Use Case:
    ![sensorDataSync](./img/sensorDataSync.png)

### 1.3 Work-flow Diagram    
    ![sensorDataSyncWF](./img/sensorDataSyncWF.png)

## 2. Scalability

### 2.1 Design Solution:
Distributed architecture where multiple instances of MonitorMe can be deployed across different servers. Implement load balancing and partitioning strategies to evenly distribute the workload and handle the maximum number of patients per physical instance.

### 2.2 Use Case:
    ![MMInstance1](./img/MMInstance1.png)

### 2.3 Work-flow Diagram    
    ![MMInstance1WF](./img/MMInstance1WF.png)


## 3. Fault Tolerance

### 3.1 Design Solution:
Implement a microservices architecture with redundant components and failover mechanisms. Utilize health checks and circuit breaker patterns to detect and recover from failures automatically.

### 3.2 Use Case:
    ![FaultDetector](./img/FaultDetector.png)

### 3.3 Work-flow Diagram    
    ![FaultDetectorWF](./img/FaultDetectorWF.png)


## 4. Security

### 4.1  Design Solution:
Implement end-to-end encryption for data transmission and storage. Use authentication and authorization mechanisms to control access to sensitive patient data. Regularly update security patches and conduct security audits to identify and mitigate potential vulnerabilities.

### 4.2 Use Case:
    ![Security](./img/Security.png)

### 4.3 Work-flow Diagram    
    ![SecurityWF](./img/SecurityWF.png)