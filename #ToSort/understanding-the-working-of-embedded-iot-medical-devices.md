# Understanding the Working of Embedded IoT Medical Devices

_Captured: 2018-08-16 at 06:51 from [dzone.com](https://dzone.com/articles/understanding-the-working-of-embedded-iot-medical?edition=387213&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-15)_

_When it comes to the healthcare industry, providing treatment and diagnosis to remote locations where doctors are not easily available or accessible is difficult. However, with the help of IoT-enabled embedded medical devices, healthcare specialists can easily identify diseases and provide treatments in a timely manner from distant locations. This article discusses how embedded IoT medical devices can change treatment methods._

With the proliferation of IoT devices, there has been a huge transformation in terms of smart cities, connected manufacturing, wireless communication, and connected healthcare. If we talk specifically about the healthcare industry, there has been a significant revolution in terms of delivering health care services in remote locations, where doctors are not easily available. Many healthcare facilities have started adopting embedded solutions for medical devices enabled with IoT to address the lack of availability of doctors in remote areas. These IoT-enabled [medical devices](https://www.einfochips.com/blog/an-overview-of-fda-regulations-for-medical-devices/) help identify diseases in patients and conduct different tests to provide an accurate and reliable treatment to patients in remote locations.

Embedded medical devices reduce the time to diagnose and treat patients effectively since these systems run on a high-speed processor with a rich operating system interface. These devices store data of each patient on the cloud and use them for different analysis and diagnosis purposes on a repetitive basis, decreasing the overall treatment turnaround.

## How Embedded IoT Medical Devices Work

IoT medical devices work by connecting to different hardware for examination purposes. The device system has a touchscreen interface for users to input data for analysis and processing. As a user inputs data related to the diseases, the system looks for symptoms pre-loaded into the file and tries to match with the provided input. If the match is found with the pre-loaded symptoms, the system responses with the disease name and generates a prescription for general medicine.

In case of a partial or no match, the system undergoes a different test based on the input given by the user and pre-loaded file, matching to identify exact disease and provide a prescription accordingly. Prescriptions and other important details are stored on the cloud-based database management solution, which can be used for future analysis. This patient information stored in the cloud can be also used for different analysis.

For example, the number of patients suffering malaria in the month of March 2018 in New York area -- the described analysis can be used to find the root cause of that particular disease in that area in the March months' time frame. The next time an outbreak occurs, the same data can be used to take precautions and reduce the number of people being affected by the same disease.

If proper disease information cannot be found by the given input and other tests performed, the system contacts the doctor with the given information. The doctor will then diagnose the patient and update the symptom and disease files for future use.

Let us now understand the workflow of IoT-enabled medical devices in detail from the following diagram:

![Image title](https://dzone.com/storage/temp/9275866-workflow-of-iot-enabled-medical-devices.jpg)

### Workflow of IoT Medical Devices

  * **User:** The user will provide the input via a touchscreen panel for the symptoms into the [embedded medical device](https://www.einfochips.com/blog/a-5-step-guide-to-risk-management-for-medical-devices/). The user also needs to provide all the personal information, such as name, contact number, age, etc. Then, the embedded device will return the generic medicine prescription for the condition found based on the input or contact the doctor if the disease is not found.
  * **Embedded Medical Device with IoT:** The embedded medical device receives inputs from the user to match the symptoms with a pre-loaded symptom file and tries to find the matching disease for same. It performs tests suggested based on the pre-loaded symptom file to get the exact match for the disease if the disease is not found by examining the symptoms. If the disease information is not found, the system involves the doctor with the given information, who will consult the user, diagnose the disease, and accordingly update the symptom file and disease file in the system. All information related to the patient and disease is stored in a cloud-based data management system. Once the disease is found, the system generates a prescription for general medicines for that particular disease. Below are the different sensors of embedded IoT medical devices to conduct various tests on patients for diagnosing the diseases: 
    * **_Glucometer:_** Glucometer is a medical device for determining the approximate concentration of glucose in the blood. A small drop of blood, obtained by pricking the skin with a lancet, is placed on a disposable test strip that the meter reads and uses to calculate the blood glucose level.
    * **_Temperature Sensor:_** This sensor allows users to measure the body temperature. It is of a great medical importance, since a number of diseases can be determined by characteristic changes in the body temperature. Likewise, the course of certain diseases can also be monitored by measuring the body temperature, and the effectiveness of the treatment initiated can be evaluated by the physician.
    * **_Blood Pressure Sensor: _**The blood pressure sensor records the patients' blood pressure in two numbers -- the systolic pressure (as the heart beats) over the diastolic pressure (as the heart relaxes between the beats).   

    * **_Airflow Sensor:_** The nasal airflow sensor is a device used to monitor the airflow rate of a patient who is in a need of respiratory help. This device consists of a flexible thread that fits behind the ears and a set of two prongs that are placed in the nostril, through which the breathing of the patient is measured.   

    * **_ECG Sensor:_** The electrocardiogram (ECG or EKG) is a diagnostic tool that is regularly used to assess the electrical and muscular functions of the heart. The electrocardiogram (ECG) has grown to be one of the most commonly used medical tests in modern medicine. It helps in the diagnosis of a myriad of cardiac pathologies, ranging from myocardial ischemia and infarction to syncope and palpitations.
    * **_EMG Sensor:_** An Electromyography (EMG) sensor measures the electrical activity of muscles at rest and during contraction. EMG signals are used in many clinical and biomedical applications. EMG is used as a diagnostics tool for identifying neuromuscular diseases, assessing low-back pain, kinesiology, and disorders of motor control. EMG signals are also used as a control signal for prosthetic devices, such as prosthetic hands, arms, and lower limbs.
  * **Prescription for General Medicines:** Based on the input provided by the user, once the disease is found by the embedded medical device, it will look for generic medicine information in the pre-loaded prescription file, mapping the disease and medication.
  * **Cloud Database Management System:** In this stage, the embedded device will store all the user details in the cloud database. This cloud-based solution can store the following information for future analysis: 
    * User's personal information
    * Information about symptoms
    * Information about tests performed and their results
    * Information about disease(s) diagnosed
    * Information about prescription and medication
    * Information about doctor's consultation, if any
    * Device information from where all data is getting logged
    * Device health information on cloud just to make sure that device is working fine, including all the sensor status and other basic information. 

Different analysis reports can be generated based on the below information stored in the cloud for future use and preventive actions.

![Image title](https://dzone.com/storage/temp/9275854-working-of-iot-medical-devices.jpg)

## Conclusion

As discussed above, the embedded IoT medical devices are helpful in the area where basic healthcare facilities are not available. Based on the disease analysis and data stored in the cloud, it helps users cure the diseases on time and also take preventive actions. However, it is important to know that a continuous network connectivity is required to integrate the medical device with the cloud.
