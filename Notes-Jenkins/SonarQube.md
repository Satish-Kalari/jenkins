# SonarQube (t3.medium with 30 GB storage)

open SonarQube in supper putty
	labauto #command in devops-practice ec2 instance will show all packages in centos 
	select tool: sonarqube (60)
	
***Public ip:9000 (for browser)***

Need to install scanner cli in sonarqube instance via supper putty
	sudo su -
	labauto
	select sonar-scanner (61)
		cd opt/sonar/bin/conf or cd opt/sonar/conf
		vim sonar-scanner.properties
		insert
		-->	un quote and edit 
				sonar.host.url=http://private.ip:9000
				sonar.login=token (see step below for token generation)
		-->	go to sonarqube my account ---> security ---> token in browser 
				under generate tokens give some nae like jenkins-agent and click generate
				copy token 
				
Sonar Scan Quality Gate:
------------------------

select quality gates in sonarqube @ Public ip:9000 
	create
		give some name like roboshop 
	add condition (for both New code & Overall Code)
		select all relevant conditions like bugs, code coverage, security rating etc.
	Apply and set as default

----do not add any conditions when practicing----
