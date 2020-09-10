# gads-cloud
This repository contains screenshots and command lines on qwiklabs completed while taking the GAD google cloud course

#### Screen shoots

![Image 1](./screenshots/lab-exercise-2.png)

![Image 2](./screenshots/lab-exercise-3.png)

![Image 1](./screenshots/lab-exercise-4.png)

![Image 1](./screenshots/lab-exercise-5.png)

![Image 1](./screenshots/lab-exercise-6.png)

![Image 1](./screenshots/lab-exercise-7.png)

![Image 1](./screenshots/lab-exercise-8.png)

![Image 1](./screenshots/lab-exercise-9.png)

![Image 1](./screenshots/lab-exercise-10.png)

![Image 1](./screenshots/lab-exercise-11.png)

![Image 1](./screenshots/lab-exercise-12.png)

![Image 1](./screenshots/lab-exercise-13.png)

![Image 1](./screenshots/lab-exercise-14.png)


--------------------------------------------------
#### Command Line Instructions
##### Lab 1
Lab link: https://googlepluralsight.qwiklabs.com/focuses/10972846?parent=lti_session

Task: Create a utility virtual mechine
gcloud beta compute --project=qwiklabs-gcp-02-1f06ff3630b3 instances create fortvest --zone=us-central1-c --machine-type=n2-standard-2 --subnet=default --no-address --maintenance-policy=MIGRATE --service-account=775255281299-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --image=debian-10-buster-v20200902 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=fortvest --no-shielded-secure-boot --no-shielded-vtpm --no-shielded-integrity-monitoring --reservation-affinity=any

##### Lab 2
Lab link: https://googlepluralsight.qwiklabs.com/focuses/10973257?parent=lti_session
Task 1: Create a vpc network and firewall rule
gcloud compute networks create privatenet --project=qwiklabs-gcp-03-e4e5428dee27 --subnet-mode=custom --bgp-routing-mode=regional

gcloud compute networks subnets create privatenet-us --project=qwiklabs-gcp-03-e4e5428dee27 --range=10.130.0.0/20 --network=privatenet --region=us-central1

gcloud compute --project=qwiklabs-gcp-03-e4e5428dee27 firewall-rules create privatenet-allow-ssh --direction=INGRESS --priority=1000 --network=privatenet --action=ALLOW --rules=tcp:22 --source-ranges=35.235.240.0/20

Task 2: Create vm instance
gcloud beta compute --project=qwiklabs-gcp-03-e4e5428dee27 instances create vm-internal --zone=us-central1-c --machine-type=n1-standard-1 --subnet=privatenet-us --no-address --maintenance-policy=MIGRATE --service-account=852311673064-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --image=debian-10-buster-v20200902 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=vm-internal --no-shielded-secure-boot --no-shielded-vtpm --no-shielded-integrity-monitoring --reservation-affinity=any

Task 3: SSH into instance
gcloud compute ssh vm-internal --zone us-central1-c --tunnel-through-iap

Task 3: Test external connectivity
ping -c 2 www.google.com

Task 4: Create a bucket
gsutil mb -l asia  gs://backup-0001

Task 5: copy items
gsutil cp gs://cloud-training/gcpnet/private/access.svg gs://backup-0001







