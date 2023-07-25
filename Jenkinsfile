pipeline {
    agent any
    parameters {
        string(name: 'PARAM_SAMPLE', defaultValue: 'This is a sample Param Value', description: 'demo!')
        choice(name: 'CHOICE_LIST', choices: ['one','two', 'three'], description: 'Choices of the list')
     }
    
    stages {
        stage('SCM trigger -update') {
            environment {
                BRANCH_NAME = 'Master-dev'
            }
            steps {
                echo 'SCM Git trigger Jenkinsfile'
                echo "branch name : ${env.BRANCH_NAME}"
            }
            post {
              success {
                echo 'Build post message has diplayed as ann example.'
              }
            }
        }
        stage('Multistage Examplee') {

            steps {
                echo 'Another Stage'
                echo "Running Job : ${JOB_NAME} with ID: ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "Params : ${params.PARAM_SAMPLE}"
            }
        }
        stage('Parameters') {
            steps {
                echo "Display CHOICE Param : ${params.CHOICE_LIST}"
            }
        }       
        stage('Input Demo!') {
            input {
                message "Should we continue??"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }        
    }
}
}
