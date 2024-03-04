# JENKINS (t3.small)

***Jenkins Redhat Packages***
	
	sudo su -
	wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
	rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
	yum install fontconfig java-17-openjdk -y 
	yum install jenkins -y 
	systemctl start jenkins 
	systemctl status jenkins
	systemctl enable jenkins
	
***take jenkins ec2 ip with 8080 to access jenkins***
run cat command the location given for password 
create our own account 

* Need to install extra plugins
	- AnsiColor
	- Pipeline Utility Steps # Need this plugin to get version
	- Nexus artifact uploader (https://plugins.jenkins.io/nexus-artifact-uploader/)
	- Rebuilder 

***Creating node:***
    Take jenkins ec2 ip with 8080 in a browser
    Go to manage jenkins and select node and add node 

	- Remote root directory
		/home/centos/jenkins-agent (/home/centos/--> is the home directory of agent ec2 instance)
	- Launch method
		launch agent via SSH
	- Host
		Private IP address of agent ec2 instance  (because both jenkins and agent ec2 instance are in same VPC)
	- Credentials
		click on +Add
			username: centos
			password: DevOps321
			ID: ssh-auth
			description: ssh-auth
	- Host Key Verification Strategy
		Non verifying verification strategy
			
# AGENT (t3.small)

    Take public ip of AGENT and access via supper putty

	sudo su 
	yum install fontconfig java-17-openjdk -y 
	exit
	mkdir jenkins-agent
	
* Installing terraform in agent: (https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

	sudo yum install -y yum-utils
	sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
	sudo yum -y install terraform

* Configuring AWS in Agent (Should Not Do in Root User, Because mater using centos)
	
	aws configure [ find IAM user at C:\Users\Satish\.aws ]
	
* Instal nodejs (To instal npm dependencies for catalogue)
	--------------
	sudo su
	dnf module disable nodejs -y
	dnf module enable nodejs:18 -y 
	dnf install nodejs -y
	
	 ***Once VPN is active assign VPN-SG to agent ec2 instance*** 