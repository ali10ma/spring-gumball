# Lab #10 - DevOps CI/CD

## CI Workflow (Part 1)

First, I started my own repository and added starter code files. Next I created new file gradle.yml and build and run workflows in repository/Actions tab. This image shows workflow successfully using the Gradle starter workflow on Github.
<img width="1920" alt="1" src="https://user-images.githubusercontent.com/60586550/204464531-e6ae1318-2f20-4a91-a53f-36ba83f69d7a.png">

This Image shows all my workflows in this repository.
<img width="1920" alt="2" src="https://user-images.githubusercontent.com/60586550/204464545-66c77cf0-65d8-4891-a003-dca33c029f5a.png">


## CD Workflow (Part 2)

https://docs.github.com/en/actions/deployment/deploying-to-your-cloud-provider/deploying-to-google-kubernetes-engineLinks to an external site.
https://cloud.google.com/iam/docs/creating-managing-service-accountsLinks to an external site.
https://kustomize.io

- Deploying to Google Kubernetes Engine 
  - Create as Standard: You manage your cluster.
<img width="1910" alt="1" src="https://user-images.githubusercontent.com/60586550/204468931-a2a2b299-051d-420e-8910-b428794e8d50.png">
  - Ensure Both APIs are Enabled: the Kubernetes Engine and Container Registry APIs.
<img width="1920" alt="enabling1" src="https://user-images.githubusercontent.com/60586550/204469109-1eed56a9-6d3a-4d59-8592-654cd52fe68f.png">
<img width="1920" alt="enabling2" src="https://user-images.githubusercontent.com/60586550/204469128-99f25826-fd23-4961-87b8-423adc0d1895.png">
<img width="1920" alt="enablingPrivate" src="https://user-images.githubusercontent.com/60586550/204469207-b7945538-adb1-4768-b1de-6f64adacd335.png">
  - cluster created:
  <img width="1920" alt="clustercreated4" src="https://user-images.githubusercontent.com/60586550/204469461-0d27dca4-2b91-48d3-b9d6-d4d6d1c37114.png">


- Set Up Secret:
  - Create a Service Account for GitHub Access and Grant Access: IAM -> Grant Acess -> 
  - New Principal: spring-gumball@cmpe172-370105.iam.gserviceaccount.com
  - Select Roles:
Kubernetes Engine Developer
Storage Admin

  <img width="1250" alt="5ServiceAccountCreatedAndGrantAccess" src="https://user-images.githubusercontent.com/60586550/204469483-34534764-6d6e-4ee5-a1a3-efa5e3904f78.png">

  - Create a JSON service account key Links to an external site.for the service account.

Navivation / IAM & Admin / IAM / Service Account

* Select Service Account "spring-gumball"
* Select Keys
* Add Key (Create New Key) -> Select JSON Key type -> Download.
  
  
 - Configure GitHub Secrets
Add the following secrets to your repository's secrets:

GKE_PROJECT: Google Cloud project ID
GKE_SA_KEY: The content of the service account JSON file
GCP Project:      cmpe172
GKE Cluster Name: cmpe172
GKE Cluster Zone: us-central1-c

GKE_PROJECT:      cmpe172-360119
SA_NAME:          spring-gumball	
SA_EMAIL:         spring-gumball@cmpe172-360119.iam.gserviceaccount.com
GKE_SA_KEY:       <exported json key file contents from GCP>
GitHub / Repo / Settings / Secrets / Action Secrets

<img width="583" alt="Screen Shot 2022-11-28 at 11 52 06 PM" src="https://user-images.githubusercontent.com/60586550/204470375-8f7b27d1-9aec-4370-b12b-d12296b62f00.png">


New Repository Secret: GKE_PROJECT
Set Value to: "Your GCP Project ID"

New Repository Secret: GKE_SA_KEY
Set Value to: "The content of the service account JSON file"

- Create .github/workflows/google.yml
and change the values for the GKE_ZONE, GKE_CLUSTER, IMAGE, and DEPLOYMENT_NAME environment variables (see example below).


Create 
  - File: kustomization.yml
  - File: deployment.yml
  - File: service.yml
  
- Trigger and Deployment to GKE
Trigger a CD Deployment by creating a new GitHub Release
6. 
<img width="1244" alt="6FinallyDeployedSuccessfullytoGKE" src="https://user-images.githubusercontent.com/60586550/204470922-ff9df303-e087-461e-8438-0df2c2454913.png">

7. 
<img width="1255" alt="7detail" src="https://user-images.githubusercontent.com/60586550/204470990-ab0b3dbe-f339-4a64-a3ac-6535749794a2.png">

8.   
  <img width="1252" alt="8details" src="https://user-images.githubusercontent.com/60586550/204471009-89206720-dfb6-424e-9d0f-e211e41b6cbf.png">



9. 
<img width="1261" alt="9allworkflows" src="https://user-images.githubusercontent.com/60586550/204471044-6db40ebd-7806-48bd-be8b-e8d54cccbabd.png">


10. Permisson Details
<img width="1256" alt="10permissiondetails" src="https://user-images.githubusercontent.com/60586550/204471158-a9f81093-d389-4a95-959a-acc4b10d7f38.png">

11. Workload Details
<img width="1259" alt="11workloaddetails" src="https://user-images.githubusercontent.com/60586550/204471193-955903d8-3e2f-4e08-9bac-b53271ebc47f.png">

12 Service Details
<img width="1262" alt="12serviceDetails" src="https://user-images.githubusercontent.com/60586550/204471282-ed348d38-9b9e-40c0-a0bf-1374e78d252c.png">

14. Ingress Details with endpoint
<img width="1920" alt="14IngressDetailswithendpoint" src="https://user-images.githubusercontent.com/60586550/204471389-c4d765fa-e62a-4a2c-897b-88e88340eddc.png">

15. Result after clicked onto endpoint link:
<img width="1920" alt="15result" src="https://user-images.githubusercontent.com/60586550/204471437-0ddffb9c-c068-4326-b656-88795a11c9b1.png">

The most difficult part for me in this lab was the permission error when build and deploying to GKE through Github because I missed in giving permisson to one of the role instead of both roles. 



  
  
  
  
