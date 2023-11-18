#Few Key Kubernetes Job Parameters

1. failedJobHistoryLimit & successfulJobsHistoryLimit: 

    Deletes the failed and successful job history based on the retention number you provide. This is super useful to trim down all failed entries when you try to list the jobs. 

    For example:
        failedJobHistoryLimit: 5  successfulJobsHistoryLimit: 10



2. backoffLimit: Total number of retries if your pod fails.


3. activeDeadlineSeconds: You can use this parameter if you want to specify a hard limit on how the time the cronjob runs. For example, if you want to run your cronjob only for one minute, you can set this to 60.
