pipeline {
    agent any
    parameters {
        string(name: 'PARAM_SAMPLE', defaultValue: 'This is a sample Param Value', description: 'demo!')
     }
    
    stages {
        stage('SCM trigger -update') {
            steps {
                echo 'SCM Git trigger Jenkinsfile'
            }
            post {
              success {
                echo 'Build post message has diplayed as an example.'
                mail to: ramprints2013@gmail.com, subject: "The pipeline Job successful! ID: ${env.BUILD_ID} on ${env.JENKINS_URL}"
              }
            }
        }
        stage('Multistage Example') {
            steps {
                echo 'Another Stage'
                echo "Running Job : ${JOB_NAME} with ID: ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh  'echo ${PARAM_SAMPLE}'
            }
        }
    }
}
