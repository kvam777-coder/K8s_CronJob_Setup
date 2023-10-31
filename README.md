# K8s_CronJob_Setup
A kubernetes CronJob is an API resource that allow to create scheduled and recurring tasks on jobs within kubernetes like just cronjob in linux. It is useful to automating periodic tasks such as batch jobs, backups and more.

Parallelism:
We can specify the number of concurrent job executions using the spec.concurrencyPolicy field. We can choose "Allow" (default) to run multiple instances of a job concurrently or "Forbid" to prevent concurrent executions.
Job Template:
A CronJob defines a template for the job to be run, including the container image, command, and other specifications. The job template is essentially a Kubernetes Pod defination file.
Retries and Backoff:
We can configure retries and backoff for failed jobs using the spec.failedJobsHistoryLimit and spec.successfulJobsHistoryLimit fields. These settings control how many job runs are retained in the history.
Timezone:
We can set the timezone for the CronJob using the spec.timezone field. This allows you to schedule jobs based on a specific timezone, which is especially useful for applications running in a distributed environment.
Suspend and Resume:
CronJobs can be easily suspended and resumed. When suspended, the scheduled jobs won’t run, but the history of previous job runs is retained. we can later resume the CronJob to continue scheduling and running jobs.
Job Cleanup:
By default, CronJobs don’t automatically clean up old job runs, but we can configure how many completed and failed jobs are retained in the history. we can also implement custom cleanup logic if needed.
Kubeconfig Access:
The CronJob controller uses the Kubernetes API to create and manage jobs. We need to ensure that the controller has appropriate kubeconfig access to create and monitor job resources.
Error Handling:
When a job run fails, the CronJob controller can notify you via events, logs, or by other means depending on your setup. You can also implement your own error handling and alerting mechanisms.
