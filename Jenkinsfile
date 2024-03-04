pipeline {
    // agent any
    agent {
        node {
            label 'AGENT-1'
        }
    } 

    // Just like variables 
    environment {
        GREETING = 'Hello Jenkins'        
    }
    
    // Terminating Build if it takes certain time
     options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds() 
    }
    // Each parameter has a Name and Value, depending on the parameter type. This information is exported as environment variables when the build starts, allowing subsequent parts of the build configuration to access those values
    parameters {
        string(name: 'PERSON', defaultValue: 'Mrs Apeksha', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    
    // BUILD
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                // echo 'Deploy'
                sh """
                    echo "Here I Wrtote Shell Script"
                    echo "$GREETING"

                """
            }
        }
        stage('check params') {
            steps {
                sh """
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
                """
            }
        }
    }

    // POST BUILD
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
         failure { 
            echo 'This runs when pipeline is failed, used set alert'
        }
         success { 
            echo 'This runs when pipeline is SUCCESS'
        }
    }
}