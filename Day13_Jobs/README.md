# Create a job
Create a job using `Initial_Job.yml` file.<br>
`kubectl create -f Initial_Job.yml`<br>
View the jobs using `kubectl get jobs`
# Delete job before completion
Create using file `Pod_Deletion.yml` file. <br>
`kubectl create -f Pod_Deletion.yml`<br>
View the pods using `kubectl get pods`
Delete the pod before the job is completed.
`kubectl get all` and see the details. We can see that a pod is recreated until the job completes.
Wait for the job to complete and delete the pod.
# Completions and Parallelism
Create jobs using file `Completion_Parallelism.yml` <br>
- **Parallelism:** Number of jobs to run at a time in parallel 
- **Completion:** Number of jobs to complete
# Error
Create job using `Error.yml` file<br>
As `ls /notexistingfolder` does not exist, the job will cause error.<br>
View `kubectl describe job <job_name>` and we can see that the pod are being re-created one by one.
# Backoff Limit
As the re-creation of pod does not stop, we need to define the maximum number of re-creations. This can be achieved by using `backoffLimit`<br>
Create job using `BackoffLimit.yml` and `watch kubectl get all`<br>
We can see that after 3rd retry, the creation of pod stops.
# Active Deadline Seconds
Sometime, we need to specify the time for our job. This is achieved by `activeDeadlineSeconds`.<br>
Create job using `ActiveDeadline.yml`. Since our job takes 60 seconds and we have defined activeDeadlineSeconds as 20, this will give error.
