pipeline {
    agent any
    parameters {
        string(name: 'PARAM_SAMPLE', defaultValue: 'This is a sample Param Value', description: 'demo!')
        choice(name: 'CHOICE_LIST', choices: ['one','two', 'three'], description: 'Choices of the list')
        choice(name: 'PLATFORM_FILTER', choices: ['all', 'linux', 'windows', 'mac'], description: 'Run on specific platform')
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
    //     stage('Input Demo!') {
    //         input {
    //             message "Should we continue??"
    //             ok "Yes, we should."
    //             submitter "alice,bob"
    //             parameters {
    //                 string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    //             }
    //         }
    //         steps {
    //             echo "Hello, ${PERSON}, nice to meet you."
    //         }        
    // }

                stage('Parallel In Sequential') {
                    parallel {
                        stage('In Parallel 1') {
                            steps {
                                echo "In Parallel 1"
                            }
                        }
                        stage('In Parallel 2') {
                            steps {
                                echo "In Parallel 2"
                            }
                        }
                    }
                }
        
        stage('BuildAndTest') {
            matrix {
                agent {
                    label "${PLATFORM}-agent"
                }
                when { anyOf {
                    expression { params.PLATFORM_FILTER == 'all' }
                    expression { params.PLATFORM_FILTER == env.PLATFORM }
                } }
                axes {
                    axis {
                        name 'PLATFORM'
                        values 'linux', 'windows', 'mac'
                    }
                    axis {
                        name 'BROWSER'
                        values 'firefox', 'chrome', 'safari', 'edge'
                    }
                }
                excludes {
                    exclude {
                        axis {
                            name 'PLATFORM'
                            values 'linux'
                        }
                        axis {
                            name 'BROWSER'
                            values 'safari'
                        }
                    }
                    exclude {
                        axis {
                            name 'PLATFORM'
                            notValues 'windows'
                        }
                        axis {
                            name 'BROWSER'
                            values 'edge'
                        }
                    }
                }
                stages {
                    stage('Build') {
                        steps {
                            echo "Do Build for ${PLATFORM} - ${BROWSER}"
                        }
                    }
                    stage('Test') {
                        steps {
                            echo "Do Test for ${PLATFORM} - ${BROWSER}"
                        }
                    }
                }
            }
        }
       
 }
}
