# Micro Services Problems

## Infrastructure Problem

- The system is able to run multiple micro services in the on-premises servers where `MonitorMe` runs and in the cloud system where `MyMedicalData` runs.

## MonitorMe Problems

- It must permit manage the access control to the data based in the roles of the medical staff.

- It must receive and the store the patient vital signals data from the last 24 hours.

- It will permits retrieve all the patient history by a time range.

- It must permit create alerts to the medical staff based in issues detected over the patient data.

## MyMedicalData Problems

- It must provides an API to permit upload snapshots of the patient data to permit store them on `MyMedicalData`.