# Deploy an application using a GitHub repo and a Dockerfile

### Dockerfile for Python Apps

```
docker login
```

Navigate to project folder and create Dockerfile to run the app. Here are the relevant Docker docs:
```
# Docker Docs: https://docs.docker.com/
# Docker Reference: https://docs.docker.com/reference/
```

For this workshop, we will use the following repository that has an example Dockerfile. MAX Object Detector is an :
```
https://github.com/IBM/MAX-Object-Detector
```

###  Get Access to Red Hat OpenShift Workshop Cluster

Use the steps below to get access to a Red Hat OpenShift cluster. 

**NOTE: Cluster Allocations are limited by time on Open Labs. Please make sure to complete the labs as soon as possible Clusters will shut down approximately 3 to 4hrs after spinning up**

1) Navigate to:

**https://developer.ibm.com/openlabs/openshift**


2) Select "Bring Your Own Application" Openlab
    <img width="1677" alt="Screen Shot 2021-09-24 at 11 46 20 PM" src="https://user-images.githubusercontent.com/25342475/134756878-ae47b2c8-4544-4e88-bf60-a9dbbc598d77.png">

3) You will be asked to sign in with your IBM account. 
   - Sign up for a IBM Cloud Account if you don't already have one [Sign up here](https://ibm.biz/Bdfgm2)
   - Sign in to your temporary RHOS cluster

###  Red Hat OpenShift Workshop Cluster

1) Once you are in the lab, open the Openshift Console
    <img width="1620" alt="Screen Shot 2021-09-25 at 12 00 03 AM" src="https://user-images.githubusercontent.com/25342475/134757147-901559ef-5583-430b-8edb-a50ef3600545.png">

2) Switch over to "Developer Mode" by selecting the option on the left side panel
    <img width="1621" alt="Screen Shot 2021-09-25 at 12 13 09 AM" src="https://user-images.githubusercontent.com/25342475/134757516-f99f66e6-fc60-487a-87eb-1cea32cbc25f.png">

3) Add a project workspace  to run your apps
    <img width="1618" alt="Screen Shot 2021-09-25 at 12 18 07 AM" src="https://user-images.githubusercontent.com/25342475/134757676-826b787b-4e5f-4fd3-b40a-c57e3320e3c4.png">

4) Create a "demo" project
    <img width="1612" alt="Screen Shot 2021-09-25 at 12 27 11 AM" src="https://user-images.githubusercontent.com/25342475/134757898-44f7aae4-5ead-4e59-a063-fd93b02823e8.png">


5) Select "Dockerfile" as the way to create an application
    <img width="1677" alt="Screen Shot 2021-09-25 at 1 32 37 PM" src="https://user-images.githubusercontent.com/25342475/134780839-f1fc3d36-dc1f-469a-9e1c-ee7a1429b6ca.png">
    

6) Set the github url to the MAX Object Detector repo and port to 5000
    <img width="1667" alt="Screen Shot 2021-09-25 at 1 35 30 PM" src="https://user-images.githubusercontent.com/25342475/134780913-0a70b5d8-9b14-4959-af0c-fe4c93055dbe.png">

7) Oila! Your Dockerfile was converted into an image that is pushed into the Openshift Image Registry and is now a running app on Openshift. Wait for the Pod's status to change to `Running` then navigate to th Network Route to launch the app.