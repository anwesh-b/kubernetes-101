# Create a Cronjob
Create a cronjob using `AutoDeletion.yml`<br>
Just watch the pods and we can see that the pods are being created. This executes the container with the commands given in the args.<br>
Cronjobs create a job that run automatically. And the job handles the rest as in `Day 13`.
<br>
# Create Cronjob with deletion specs
As the default Cronjobs stores 3 pods, we can minimize or maximize it by using `successfulJobsHistoryLimit` and `failedJobsHistoryLimit` which defines number of pods to store for successful and failed jobs.<br>
`kubectl create -f AutoDeletion.yml` to create a new cronjob. <br>
`kubectl get all` and see that we only get history of one successful pod.
<br><br>
Apart form these, we can set 
- Starting Deadline: Maximum time to reexecute the job if missed
- Job Template: Template for the Job
- Concurrent Policy: How to treat concurrent Jobs: allow (default), reject or replace
- Suspend: To suspend the subsequent executions or not: true or false(default)

For more info, go <a href="https://kubernetes.io/docs/tasks/job/automated-tasks-with-cron-jobs/">here</a>