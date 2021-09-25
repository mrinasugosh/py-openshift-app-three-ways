# Deploy an Python App using image in a external registry (ie Dockerhub)

### Build and Push Docker Image to External Registry

```
docker login
```

Navigate to project folder with Docker file and run the following commands:
```
docker build -f Dockerfile -t hello-python:latest .

# Docker Docs: https://docs.docker.com/
# Docker Reference: https://docs.docker.com/reference/
```

```
docker image tag ${REMOTE_APP_NAME}:latest ${LOCAL_APP_NAME}:latest
```

```
docker image push ${REMOTE_APP_NAME}:latest
```

Once this is done your app should be up in your private registry on DockerHub. The example we will use the following image on Dockerhub:
```
docker.io/mrinasugosh/sample-python-app
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

###  Open Red Hat OpenShift Workshop Cluster

1) Once you are in the lab, open the Openshift Console
    <img width="1620" alt="Screen Shot 2021-09-25 at 12 00 03 AM" src="https://user-images.githubusercontent.com/25342475/134757147-901559ef-5583-430b-8edb-a50ef3600545.png">

2) Switch over to "Developer Mode" by selecting the option on the left side panel
    <img width="1621" alt="Screen Shot 2021-09-25 at 12 13 09 AM" src="https://user-images.githubusercontent.com/25342475/134757516-f99f66e6-fc60-487a-87eb-1cea32cbc25f.png">

3) Add a project workspace  to run your apps
    <img width="1618" alt="Screen Shot 2021-09-25 at 12 18 07 AM" src="https://user-images.githubusercontent.com/25342475/134757676-826b787b-4e5f-4fd3-b40a-c57e3320e3c4.png">

4) Create a "demo" project
    <img width="1612" alt="Screen Shot 2021-09-25 at 12 27 11 AM" src="https://user-images.githubusercontent.com/25342475/134757898-44f7aae4-5ead-4e59-a063-fd93b02823e8.png">


5) Select "Container Image" as the way to create an application
    <img width="1610" alt="Screen Shot 2021-09-25 at 12 33 20 AM" src="https://user-images.githubusercontent.com/25342475/134758190-ecd23d23-3954-46be-b1ca-374904357fc2.png">

6) Type in the relevant image reference under "Image name for external reegistry"
    <img width="1674" alt="Screen Shot 2021-09-25 at 12 41 55 AM" src="https://user-images.githubusercontent.com/25342475/134758401-243d4444-28e2-4c6f-bb83-7d44f69cba27.png">

7) Oila! You have deployed your image as a running app on Openshift. Wait for the Pod's status to change to `Running` then navigate to th Network Route to launch the app