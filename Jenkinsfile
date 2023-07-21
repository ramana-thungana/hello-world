pipeline {
    agent any
    stages {
        stage('SCM trigger -auto') {
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
            }
        }
    }
}
