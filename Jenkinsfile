pipeline {
    agent any
    stages {
        stage('SCM trigger -update') {
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
                echo "Running Job : ${JOB_NAME} with ID: ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
}
