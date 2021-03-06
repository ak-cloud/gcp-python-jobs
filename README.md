
# gcp-python-jobs
This repo cotains common python Cloud functions to do admin jobs in GCP. 


start/Stop-VM-Instance: GCP stop/start/restart Compute Engine resources on a schedule

It's an utility function to stop all VM instances in a project. This can be used with Pub/Sub topic to stop VM instances when not needed and startup when needed. Typically with Cloud Scheduler you can deploy this script as cloud function and stop all your VMs at a given time. It tries to achieve following pattern:

![alt text](https://github.com/abharku/gcp-python-jobs/blob/master/GCP_cloud_scheduler.png)

Use the input.json file to send input to stop/start All VMs on a schedule. Change these values in your input.json

project = Name of the project in which VMs are deployed

regions = Array of json object which lists all regions you have your VMs defined in

regions["zones"] = You can also specify list of zones your servers are in. Not all regions provide a,b,c zone

filter= A string to filter VMs you will like to stop start. The string can be any part of your VM name.

Cloud Scheduler(https://cloud.google.com/scheduler/), GCP’s fully managed cron job scheduler, provides a straightforward solution for automatically stopping and starting VMs. By employing Cloud Scheduler with Cloud Pub/Sub (https://cloud.google.com/pubsub) to trigger Cloud Functions on schedule, you can stop and start groups of VMs identified with labels of your choice (created in Compute Engine). 
