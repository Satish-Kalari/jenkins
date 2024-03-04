# Jenkins Shared Libraries 
(https://www.jenkins.io/doc/book/pipeline/shared-libraries/)
-------------------------
Go to jenkins browser 
		---> manage jenkins 
			----> system 
				----> Global Pipeline Libraries
					----> add
							Name: o-robo-shared-library [your-shared-library-folder-name]
							default version: master
							Retrivel method
								modern SCM
									source code management: git
										project repository: git-hub url for repo robo-shared-library 
							save	