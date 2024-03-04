# Nexus (t3.medium with 30 GB storage)
devops-practice  AMI 
(https://help.sonatype.com/en/installation-methods.html)

***Nexus is popular artifact repository (Not for code)***
***Git is popular code repository (Not for Artifacts)***

* Take public ip for nexus ec2 instance and access via supper putty
    sudo su
	labauto #command ec2 instance will show all packages in centos 
	select tool: nexus
	choose option 2 from list 
	after installation of nexus 
		netstat -lntp
		watch netstat -lntp
		systemctl status nexus 
cd ..
cd nexus/sonatype-work/nexus3/log 
less nexus.log --> to check status of nexus

***take ec2 instance ip with 8081 to access nexus*** 

--->click on server administration and configuration
		- select create repository
		- maven2 (hosted)
			- version policy: Mixed
			- Layout Policy: Permissive
			- Deployment Policy: Allow redeploy
			- Save
---> add nexus-auth in jenkins credentials
		- go to jenkins page in browser
		- manage jenkins
		- credentials
		- global credentials
		- add credentials
			- username: admin (nexus login ID)
			- password: admin123 (nexus password)	
			- ID: nexus-auth
			- description: nexus-auth
			- create

zip -q -r catalogue.zip ./* -x ".git" -x "*.zip"
	here 
		./* means all the files in that directory
		-x means exclude 
		-q means quite zip log output 