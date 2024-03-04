# Auto Trigger Jenkins Pipelines
https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project

If developer pushes the code into git, jenkins should automatically trigger a pipeline  

***In GitHub***
go to repo from which we need auto trigger
    - select settings 
        - choose webhook
            - add webhook
                - <jenkins-url:8080>/github-webhook/ 
                - Content type’ select: ‘application/json’ and leave the ‘Secret’ field empty.
                - Which events would you like to trigger this webhook?
                    select Pushes
                - click on "Add Webhook"
***In jenkins***
In pipeline configuration under Build Triggers
    - In Jenkins, click on ‘New Item’ to create a new project.
    - Give your project a name
    - Click on the ‘Source Code Management’ tab
    - Click on Git and paste your GitHub repository URL in the ‘Repository URL’ field.
    - Click on the ‘Build Triggers’ tab and then on the ‘GitHub hook trigger for GITScm polling’. 
    -  Apply and save 