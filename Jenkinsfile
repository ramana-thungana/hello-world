pipeline {
    agent any
    environment { 
        CC = 'clang'
    }
    stages {
        stage('SCM trigger -update') {
            environment {
              DEBUG_FLAGS = "A Sampe debug variable ENV."
            }

            steps {
                echo 'SCM Git trigger Jenkinsfile'
            }
            post {
              success {
                echo 'Build post message has diplayed as an example.'
              }
            }
        }
        stage('Multistage Example') {
            steps {
                echo 'Another Stage'
                echo "Running Job : ${JOB_NAME} with ID: ${env.BUILD_ID} on ${env.JENKINS_URL} debug:: ${DEBUG_FLAGS}"
            }
        }
    }
}
