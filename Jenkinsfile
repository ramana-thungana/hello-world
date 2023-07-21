pipeline {
    agent any
    parameters {
        string(name: 'PARAM_SAMPLE', defaultValue: 'This is a sample Param Value', description: 'demo!')
     }
    
    stages {
        stage('SCM trigger -update') {
           agent { 
                label 'linux SCM'
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
            agent { 
                label 'MUltistage Label'
            }
            steps {
                echo 'Another Stage'
                echo "Running Job : ${JOB_NAME} with ID: ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh  'echo ${PARAM_SAMPLE}'
            }
        }
    }
}
