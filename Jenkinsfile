pipeline {
     agent { 
        label 'ANSIBLE' 
        }

    environment {
        ENV_URL = "pipeline.global.com"
        SSH_CRED =  credentials('SSH_CRED')
    }

    options {
    buildDiscarder(logRotator(numToKeepStr: '3')) 
    disableConcurrentBuilds()
    disableResume()
}

parameters {
        string(name: 'PERSON', defaultValue: 'Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage ('One') {
            steps {
            echo "I AM STAGE ONE STEP"
            echo "Environment URL is ${ENV_URL}"
            sh "hostname"
            }
            }

        stage ('Two') {
            environment {
        ENV_URL = "stage2.global.com"
        }
        steps {
             echo "I AM STAGE TWO STEP"           
            echo "Environment URL is ${ENV_URL}"
            }
            }

        stage ('Three') {
            steps {
             echo "I AM STAGE THREE STEP"    
             sh 'env'     
            }
            }

        }
}
