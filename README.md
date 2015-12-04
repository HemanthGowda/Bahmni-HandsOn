Bahmni Hands On
===============

This is a set of exercises that we can go through to understand how Bahmni can be configured. 

Theme: Lets create a new workflow for a hospital that primarily deals with emergency care. 

Exercises
---------

 **1. Create an emergency registration app**
 
 Create an app called Emergency in the home page once you login. On click, it should take you to the existing registration app. Have a nice logo, if you can. 

 Documentation for [Home Module](https://bahmni.atlassian.net/wiki/display/BAH/Home+Module)

 
 **2. Change default visit type from OPD to EMERGENCY**

Go to the new Emergency App that we created. Click the "Create New" button. Notice that the button at the bottom defaults to Start OPD Visit. We will change this to default to “Start EMERGENCY Visit” instead. 

Documentation for [Registration App](https://bahmni.atlassian.net/wiki/display/BAH/Registration+App)

Hint: Take a look at /var/www/bahmni_config/openmrs/apps/registration/app.json, specifically the line

      “defaultVisitType”: “OPD"


 **3. Go to consultation after registering a patient.**

Emergency registration are being performed by clinicians who need to directly go to the consultation screen after registering a patient. The consultation screen is available in the clinical app. Try registering a patient, then going through the clinical app and opening the patient. You will get an option to start consultation for the patient. 
https://<ip>/bahmni/clinical/#/default/patient/{patientUuid}/dashboard/concept-set-group/observations
 
Documentation to [configure a forward url](https://bahmni.atlassian.net/wiki/display/BAH/Registration+Page#RegistrationPage-Registration2ndPage)


 **4. Create a new Observation Template**

On the observations tab of the clinical app, there are multiple templates/forms that can be filled. These are setup as concept sets in OpenMRS. A basic version of the template can be created by creating a concept set and attaching them to a special concept called "All Observation Templates". You can, alternatively, use the admin app to upload a concept set via csv. 
Lets create a new observation template to capture ECG results. A sample csv is available [here](https://github.com/HemanthGowda/Bahmni-HandsOn/tree/master/ECG-CSV). Make sure you upload the concepts.csv before concept_set.csv. 

Documentation to [import a csv](https://bahmni.atlassian.net/wiki/display/BAH/Create+a+New+Observation+Form#CreateaNewObservationForm-AddObservationFormstoBahmni)

 
 **5. Make a field autocomplete**

Once we are done with importing ECG template. Lets make one of the field in that template a autocomplete field. Make sure you can make only coded concept field as autocomplete.
We have two fields in ECG template which can be converted to autocomplete. Those are: "Type Of Visit",  "Rhythm".
To make a field autocomplete copy the following config into conceptSetUI section under app.json of clinical module.

    “<Concept Fully Specified Name>" : {
        “autocomplete" : true,
    }
    
 **6. Show the ECG template on the patient dashboard.**

Bahmni allows configuration of several types of dashboards. One such is the patient dashboard. You will find a link to the dashboard from the consultation page that we just linked to the Emergency app. It consists of different sections (called display controls) that can be configured to show specific pieces of information about a patient. 
Lets configure a new "ObservationControl" on the "General" patient dashboard to show data from the ECG template that we set up. 

Configuration to configure a [display control](https://bahmni.atlassian.net/wiki/display/BAH/Display+Controls+Configuration#DisplayControlsConfiguration-ObservationControl)

 
 **7. Configure a new patient dashboard**

You can create your own dashboard if you want to. Lets move the ECG template we just created into a new Emergency dashboard. 

Documentation for [patient dashboards](https://bahmni.atlassian.net/wiki/display/BAH/Configure+Patient+Dashboard)


 **8. Setup Default visit type based on login location**

In Step 2, we created a default visit type. It is also possible to configure default visit types based on the login location of a user. Lets limit making the default visit type to OPD only for a login location of OPD-1. 

Documentation available [here](https://bahmni.atlassian.net/wiki/display/BAH/Configure+Patient+Registration#ConfigurePatientRegistration-4.ConfigureVisits )
