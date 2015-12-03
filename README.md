


Bahmni Hands On
===============

Level 1:
--------
 **1. Create an emergency registration app**
To complete this task, you will need to have an app called Emergency in the home page once you login. Onclick, it should take you to the existing registration app. For more details, please see
     https://bahmni.atlassian.net/wiki/display/BAH/Home+Module
     
 **2. Change default visit type from OPD to EMERGENCY**
 Go to the new Emergency App that we created. Go to Create New. Notice that the button at the bottom defaults to Start OPD Visit. We will change this to default to “Start EMERGENCY Visit” instead. 
Take a look at /var/www/bahmni_config/openmrs/apps/registration/app.json, specifically the line

      “defaultVisitType”: “OPD"

Configuration for the registration app is available in the following link.
https://bahmni.atlassian.net/wiki/display/BAH/Registration+App

 **3. Go to consultation after registering a patient.**
 Emergency registration are being performed by clinicians who need to directly go to the consultation screen. The consultation screen is available in the clinical app. Try registering a patient, then going through the clinical app and opening the patient. You will get an option to start consultation for the patient. 
 https://<ip>/bahmni/clinical/#/default/patient/{patientUuid}/dashboard/concept-set-group/observations
 
Follow link to configure a forward url
https://bahmni.atlassian.net/wiki/display/BAH/Registration+Page#RegistrationPage-Registration2ndPage

 **4. Upload a concept set (for adding to observation template)**
 To complete this task you have to upload a ECG template to the system.
 You can find CSV file from following link.
 https://github.com/HemanthGowda/Bahmni-HandsOn/tree/master/ECG-CSV
 Make sure you upload the concepts.csv before concept_set.csv.

Follow below link to know how to import csv.
https://bahmni.atlassian.net/wiki/display/BAH/Create+a+New+Observation+Form#CreateaNewObservationForm-AddObservationFormstoBahmni
 
 **5. Make a field autocomplete**
 You can make an coded concept as autocomplete when there is a lot of answers to that.
 To make a field autocomplete copy the following config into conceptSetUI section under app.json of clinlical

       “<Concept Full Name>" : {
			“autocomplete" : true,
       	}
Make sure the Concept is Coded.

 **6. Configure a display control for the ECG.**
 To complete this task you have to configure a new section in patient dashboard which shows the data from ECG template.
 To know how to configure display controls follow the link:
 https://bahmni.atlassian.net/wiki/display/BAH/Display+Controls+Configuration#DisplayControlsConfiguration-ObservationControl
 
Level 2:
--------
**1. Configure a new patient dashboard**

Follow link to configure patient dashboard.
https://bahmni.atlassian.net/wiki/display/BAH/Configure+Patient+Dashboard

**2. Setup Default visit type based on login location (We’ll demo)**

Below documentation link explains how to configure visit type based on login location.
https://bahmni.atlassian.net/wiki/display/BAH/Configure+Patient+Registration#ConfigurePatientRegistration-4.ConfigureVisits 
