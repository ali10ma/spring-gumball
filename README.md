Part 1 CI Workflow

For this part it was pretty simple, I just made my own repo and added the starter code. I then created a workflow with gradle and updated the depoloyment file to make it build and the screenshots below show that it built perfectly.
![alt text](screenshots/01CiWorkflow.png)
![alt text](screenshots/02workflow.png)

-
-
Part 2 Workflow GKE
For this part, first I created a workflow with gke and made the needed changes to the google.yml file to ensure it worked. Below three screenshots my creation of a key process. First screenshot shows the making of the service account, then making of the key and lastly creating the secrets in github. I had a little trouble here because I put cmpe 172 as the project name and that did not work, I needed to add the id of cmpe 172 to work properly.
![alt text](screenshots/03key.png)
![alt text](screenshots/04key.png)
![alt text](screenshots/05key.png)

-
-
I then started up my cluster and below the screenshot shows it. When creating the cluster I followed whatever the google.yml file said and filled it in accordingly.
![alt text](screenshots/06cluster.png)

To trigger a build I had to make a new release, by clicking on draft a new release and filling in 1.0 and that is show with the first screenshot and then the one after shows the workflow being built. The last two screenshots show the build process and it went fine and got a green check.
![alt text](screenshots/07release.png)
![alt text](screenshots/08release.png)
![alt text](screenshots/09release.png)
![alt text](screenshots/10release.png)

-
-
These next 4 screenshots show the the pods being confirmed, the workloads and service. Then I created an ingress for the load balancer and the last screenshots shows it.
![alt text](screenshots/11confirmpods.png)
![alt text](screenshots/12workloads.png)
![alt text](screenshots/13service.png)
![alt text](screenshots/14ingress.png)

-
-
Lastly it worked perfectly and the gumball image showed up!!
![alt text](screenshots/15gumball.png)

-
-
I didn't have many issues in this lab, only issue of mine was to make sure everything was spelled correctly and the json file was copied properly. Only issue was that I was confused on which project name to put and the cmpe172 was not the right one but the cmpe172-######, or the identification number worked perfectly
