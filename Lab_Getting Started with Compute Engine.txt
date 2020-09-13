#Lab: Google Cloud Fundamentals:Getting Started with Compute Engine.

// Objectives:
In this lab, you will learn how to perform the following tasks.
- Create a compute Engine virtual machine(vm) using the Google Cloud Platform(GCP)console.
- Create a compute Engine virtual machine(vm) using gcloud command-line-interface.
- Connect between instances.

// Steps: 
1. create a compute Engine virtual machine using the Google Cloud Platform(GCP) console.
   gcloud compute instances create my-vm-1 --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default" --tag http.  
  gcloud compute firewall-rules create  allow http --action=ALLOW --destination=INGRESS --rules=https:80 --target-tags http.

2. Create a Compute Engine virtual machine using the gcloud command line interface.
  gcloud config set compute/zone us-central-b.
  gcloud compute instances create my-vm-2 --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default".

3. Connect between the two instances.
Use the ping command  to confirm that my-vm-2 can reach my-vm-1 over the network.

- connect to my-vm-2:
   gcloud cvompute ssh my-vm-2
- ping my-vm-1 from my-vm-2:
   ping-c 4 my-vm-1
- Use the ssh command to open a command prompt on my-vm-1 from my-vm-2:
  ssh my-vm-1   
-  At the command prompt on my-vm-1, install the Nginx webserver:
   sudo nano/var/www/html/index.Nginx-debian-html.
- Use the arrow keys to move the cursor to the line just 
  below the h1 header
-Add text like this and replace YOUR_NAME with [YOUR_NAME]

    Hi from Chidozie Franklin!
  Save with ctrl+O enter and ctrl+x to exit the editor. comfirm that the webserver is serving your new page.

-At the command prompt on my-vm-1, execute the command:


     curl http://localhost/

-Result:
  The response will be the html source of the webserver's 
  homepage, including your line of customize text.

- To exit the command prompt on my-vm-1, run this command:
  exit

- To confirm that my-vm-2 can reach the webserver on my-vm- 
 1, on the command prompt of my-vm-2, run this command:

  curl http://my-vm-1/