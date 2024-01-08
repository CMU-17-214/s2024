# Lab 12 - Cloud Deployment

Repo link: [https://github.com/CMU-17-214/f23-rec12-fixed](https://github.com/CMU-17-214/f23-rec12-fixed)

In this recitation, you will deploy a version of the TicTacToe game to the
Google Cloud Compute Engine service, allowing you to access it remotely. You can use the same strategy if you want to release your Santorini implementation publicly.

## Deliverables
- [ ] Enable the Google Cloud Compute Engine service, and create a virtual machine.
- [ ] Successfully run a Docker image on your cloud virtual machine and show the running site to the TA.
- [ ] Make a change to the code and update the image on the cloud.

## Introduction
One of the services provided by Google (and Amazon, Microsoft, etc.) is the
ability to use servers that they have as _virtual machines_. This allows you to
skip a lot of the work needed to assemble your own server, connect it to the
internet, and maintain hardware that might fail. It also allows you to quickly deploy web applications and observe changes as you make them.

The instructions here are highly manual, and almost all of them can be automated. 
This is out of the scope of this course, but other CMU courses focused on DevOps or cloud computing (e.g., 17-346/646, 15-319/619) go into more depth on modern tooling to automate them.

## Instructions

### Fork the starter repository

1. Create your own fork of [the starter repository](https://github.com/CMU-17-214/f23-rec12-fixed).

### Setting up a new virtual machine
We continue to use the Google Cloud Platform as in Lab 8 and HW5, for which we provided coupons to get free credits. NOTE: We do not have any additional backup coupons. If you have not yet resolved coupon issues, you will not be able to complete this portion of the lab or have to use another billing account. 


You may or may not have Google Cloud APIs enabled that you need for these
steps. If you do not, choose "Enable" when prompted.

2. On the [Google Cloud Console](https://console.cloud.google.com), click the
   "Create a VM" button.

![createvm](images/lab12/create-a-vm.png)

3. Give your VM a name.

4. It is ok to use the default E2 machines, but under the "Machine type"
   dropdown select `e2-small`

![selectvm](images/lab12/select-vm.png)

5. Under "Firewall", select the boxes for "Allow HTTP traffic" and "Allow HTTPS
   traffic".

![selecttraffic](images/lab12/select-traffic.png)

6. Click "Create".

7. You will be brought to a screen with a list of VM instances, and should see
your newly created VM, together with an "External IP" that you can use to
connect to it (in this case it's 34.69.81.171).

![details](images/lab12/details.png)

### Connecting to your virtual machine
Similar to lab 8 and homework 5, you will be using the Google Cloud CLI `gcloud`
to run these commands. If you do not have it set up properly, please refer back
to the lab 8 instructions.

8. On your local machine, run `gcloud init` to make sure you are logged in to
   the Google Cloud service.

9. Log in to your virtual machine with `gcloud compute ssh
   --project=[YOUR_PROJECT_NAME] [YOUR_VM_NAME]`

10. We will be using Docker to deploy this lab. Install the latest version of
   Docker on the remote machine using [the instructions
   here](https://docs.docker.com/engine/install/debian/#install-using-the-repository).

### Sign up for a Docker account and set up a new repository

11. Create a new account on [https://hub.docker.com](https://hub.docker.com). This will be used for
creating Docker images and pushing them to Docker Hub for deployment to your new
virtual machine.

12. Sign in to Docker Hub. Once you are signed in select "Create repository". For
the name, select something reletavely memorable (e.g., "lab12"). We do not
recommend creating a private repository, or you will have to sign in to your
docker account on the virtual machine as well.

### Install Docker on your local computer

For this lab, we will be compiling, containerizing, and deploying an app to
Docker Hub locally so that they can be easily deployed to the cloud. Note: IF AT
ANY TIME YOU RUN INTO ISSUES HERE, PLEASE JUMP TO THE [EMERGENCY BAILOUT
INSTRUCTIONS](#emergency-bailout-instructions) below. These instructions are
tested and use the virtual machine itself for compilation and containerization,
which is a much less realistic use case, but should allow you to complete the lab.

13. Download the Docker Desktop installer from the [Docker Desktop
website](https://docs.docker.com/desktop/), and follow the instructions to
install it.

14. From Docker Desktop, sign in to your account using the credentials you
created in the previous step.

### Build and deploy a Docker container
15. On your local machine, clone the repository you forked, and follow the instructions in its README.md to build a Docker image.

16. You should be able to see the Docker image you just created with `docker images`.

17. Now create a new Docker tag matching your Docker Hub repository name. To do this run
`docker tag lab12
[dockerhub-user-name]/[repository-name]`. `[dockerhub-user-name]/[repository-name]`
should match your user name and the repository name you created on Docker Hub.

18. Check that the images you created exist with `docker images`. You should see
two images under the `REPOSITORY` column corresponding to the two you just
created.

19. Push the `[dockerhub-user-name]/[repository-name]` image to Docker Hub with
`docker push [dockerhub-user-name]/[repository-name]`.


### Pull the image from Docker Hub on the Google Cloud VM
20. Log back into the Google Cloud VM you created earlier with the `gcloud compute ssh` command from step 9.

21. Download the image you just pushed to Docker Hub onto the VM using `docker pull
[dockerhub-user-name]/[repository-name]`. Check that it exists using `docker
images`.

24. Run the Docker image you just pulled with `docker run -p 80:8080
[dockerhub-user-name]/[repository-name]`. The parameter `-p 80:8080` maps port 8080 of the virtual machine to port 80 of your local machine. You should see the message "Running on
port 8080!" if it is successful and should be able to access the game locally on port 80 (i.e., just `http://<IP>`).

25. Navigate your web browser to the IP address of the container you created
earlier (i.e., the IP from step 7). You should see the same TicTacToe interface from Lab 7. Skip to step 30 if you got to this point successfully.

### EMERGENCY BAILOUT INSTRUCTIONS

If it turns out that you are having trouble setting up Docker locally, you do
have a virtual Linux machine that you can use to build the Docker
image. Although this is an unrealistic use case, you can get set up with a
container following these instructions.

26. Log in to the VM you started on Google Cloud with the `gcloud compute ssh` command from step 9 above. Since you'll be compiling on
the VM, you should first install the additional dependencies using `apt install
maven openjdk-17-jdk nodejs npm`.

27. Clone your fork of the starter repository to the Google Cloud VM. Follow the instructions in its README.md to build a Docker image. You do not need to interact with Docker Hub with this method.

28. Run the Docker image you just created with `docker run -p 80:8080 lab12`.

29. Navigate your web browser to the IP address of the container you created earlier (i.e., the IP from step 7). You should see the same TicTacToe interface from Lab 7.

### Make a change to the code
Before you make a change, you can use Ctrl-C to kill the running Docker image on your VM.

30. In the forked repository, edit the last line of `front-end/src/App.css` to make playable cells `blue` instead of `red`. 
*If you followed the Emergency Bailout Instructions above*, you should make this change on your local computer, commit it, and push it to GitHub. Then, from the Google Cloud VM you can do a `git pull` and the code will be updated.

31. From the machine you built the image on, re-build the front end by running `npm run compile` in the `front-end` directory.

32. Re-build the Docker image using `docker build -t lab12 --platform linux/amd64 .`. *If you followed the Emergency Bailout Instructions above, skip the next step.

33. Update the tag, push to Docker hub, and pull the new image from Docker hub following steps 17 through 21 above.

34. Re-run the docker image you just created on the VM using `docker run`. You should see the new website running when you point your web browser to the IP address of the container.

---

Remember to shut down the virtual machine if you do not need it anymore to stop paying credits for it.
