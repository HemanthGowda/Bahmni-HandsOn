Bahmni Hands On
===============

This is a set of exercises that we can go through to understand how Bahmni can be configured. 

Theme: Lets create a new workflow for a hospital that primarily deals with emergency care. 

Exercises
=========

 **1. Create an emergency registration app**
 
 Create an app called Emergency in the home page once you login. On click, it should take you to the existing registration app. Have a nice logo, if you can. 

 Documentation for [Home Module](https://bahmni.atlassian.net/wiki/display/BAH/Home+Module)

 
 **2. Change default visit type from OPD to EMERGENCY**

Go to the new Emergency App that we created. Click the "Create New" button. Notice that the button at the bottom defaults to Start OPD Visit. We will change this to default to “Start EMERGENCY Visit” instead. 

Documentation for [Registration App](https://bahmni.atlassian.net/wiki/display/BAH/Registration+App)

Hint: Take a look at /var/www/bahmni_config/openmrs/apps/registration/app.json, specifically the line

      “defaultVisitType”: “OPD"


 **3. Go to consultation after registering a patient.**

Emergency registration are being performed by clinicians who need to directly go to the consultation screen. The consultation screen is available in the clinical app. Try registering a patient, then going through the clinical app and opening the patient. You will get an option to start consultation for the patient. 
https://<ip>/bahmni/clinical/#/default/patient/{patientUuid}/dashboard/concept-set-group/observations
 
Documentation to [configure a forward url](https://bahmni.atlassian.net/wiki/display/BAH/Registration+Page#RegistrationPage-Registration2ndPage)


 **4. Upload a concept set (for adding to observation template)**

To complete this task you have to upload a ECG template to the system.
A sample csv is available [here](https://github.com/HemanthGowda/Bahmni-HandsOn/tree/master/ECG-CSV). Make sure you upload the concepts.csv before concept_set.csv. See what changes on the consultation tab once the upload is complete. 

Documentation to [import a csv](https://bahmni.atlassian.net/wiki/display/BAH/Create+a+New+Observation+Form#CreateaNewObservationForm-AddObservationFormstoBahmni)

 
 **5. Make a field autocomplete**

You can make an coded concept as autocomplete when there is a lot of answers to that.
To make a field autocomplete copy the following config into conceptSetUI section under app.json of clinlical

       “<Concept Full Name>" : {
			“autocomplete" : true,
       	}
Make sure the Concept is Coded.

 **6. Configure a display control for the ECG on the Patient Dashboard.**

Bahmni allows configuration of several types of dashboards. One such is the patient dashboard. You will find a link to the dashboard from the consultation page that we just linked to the Emergency app. Lets configure a new section on the patient dashboard to show data from the ECG template that we set up. 

Configuration to configure a [display control](https://bahmni.atlassian.net/wiki/display/BAH/Display+Controls+Configuration#DisplayControlsConfiguration-ObservationControl)

 
 **7. Configure a new patient dashboard**

Documentation for [patient dashboards](https://bahmni.atlassian.net/wiki/display/BAH/Configure+Patient+Dashboard)


 **8. Setup Default visit type based on login location**

Documentation available [here](https://bahmni.atlassian.net/wiki/display/BAH/Configure+Patient+Registration#ConfigurePatientRegistration-4.ConfigureVisits )

