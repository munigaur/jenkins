pipeline {
    agent any

    environment {
        ENV_URL = "pipeline.global.com"
        SSH_CRED =  credentials('SSH_CRED')
    }

    options{
    buildDiscarder(logRotator(numToKeepStr: '3')) 
    disableConcurrentBuilds()
    disableResume()
    timeout(time: 1, unit: 'MINUTES')
}

    }
    stages {
        stage ('One') {
            steps {
            echo "I AM STAGE ONE STEP"
            echo "Environment URL is ${ENV_URL}"
            sleep 300
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
