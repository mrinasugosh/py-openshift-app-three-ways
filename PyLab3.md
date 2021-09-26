# Deploy the application using a GitHub repo with OpenShift CLI

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

1) Once you are in the lab, login to Openshift Cluster in the CLI. 
    ```
    oc login --server https://c100-e.us-east.containers.cloud.ibm.com:32581 -u apikey -p ${API_KEY}
    ```
    This command will be availble under the `Quick Links and Common Commands` tab:
        <img width="1680" alt="Screen Shot 2021-09-26 at 4 11 23 PM" src="https://user-images.githubusercontent.com/25342475/134822660-63d53b08-df84-446e-9ed7-c7ba575f86f0.png">


2) Let's deploy the app. All you  have to do is create new app in the project and Openshift will handle the rest:
    ```
    oc new-app https://github.com/IBM/MAX-Object-Detector
    ```
    TLDR: Using the new-app results in a build configuration, which creates a new application image from your source code. It also constructs a deployment configuration to deploy the new image, and a service to provide load-balanced access to the deployment running your image. Notice that we didn't even specify the build strategy? OpenShift automatically detects whether the Docker or Source build strategy is being used, and in the case of Source builds, detects an appropriate language builder image.
    <img width="1641" alt="Screen Shot 2021-09-26 at 4 19 54 PM" src="https://user-images.githubusercontent.com/25342475/134822839-3dce6890-dd37-4d7a-9f9f-3516aaa2221e.png">

3) Since this is a web application that will reach end users we need a route to expose this app. An OpenShift Container Platform `route` exposes a service at a secure host name, like `www.example.com`, so that external clients can reach it by name. To do this we simply run:
    ```
    oc expose svc/max-object-detector
    ```

4) Now to access the route where our app is hosted we will run the get routes command:
    ```
    oc get routes
    ```
    <img width="1667" alt="Screen Shot 2021-09-26 at 4 24 48 PM" src="https://user-images.githubusercontent.com/25342475/134822987-8be30b24-23cb-4f0c-8c5b-cde45b21bc5b.png">
    
    In this example the route url would be `http://max-object-detector-default.dte-ocp46-kcwjv9-915b3b336cabec458a7c7ec2aa7c625f-0000.us-east.containers.appdomain.cloud`  

5) Navigate to the route and Oila! Your github repo's code was put into an image that is pushed into your own private Openshift Image Registry and is now a running app on Openshift. Launch the app and have fun exploring:
    <img width="1678" alt="Screen Shot 2021-09-26 at 4 28 07 PM" src="https://user-images.githubusercontent.com/25342475/134823089-fd89acf7-4120-40ff-9bc0-b3c3152e448f.png">