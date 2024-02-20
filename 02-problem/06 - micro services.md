
# Requirements
The system should be able to adjust its alerts based on the patient's sleep status.
The system should be able to upload patient snapshots to MyMedicalData through a secure HTTP API call.

The system is able to run multiple micro serivce programs,
Here we implement 2 types of microservices:
1. runs on MonitorMe, the system pull micro service program from cloud, install locally, this allows to use internal data without sharing privacy
2. runs on MyMedicalData the cloud, the system push snapshot of patient data to the

# Privacy policy profiles
different kind of profiles are made for choise according with different types of microservices, so we offer various options to patients.
