pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo "${env.BUILD_NUMBER}"
                echo "${env.BUILD_URL}"
            }
        }

        Stage('Prod Approval'){
            steps{
                script{
                    if (env.BRANCH_NAME == "master") {
                        input ('proceed for prod deployment?')
                    }    
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
            post {
                failure{
                    echo 'sending notification'
                }
            } 


        }
    }

    post {
         always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
         }
         success {
            echo 'I succeeded!'
         }
         unstable {
            echo 'I am unstable :/'
         }
         failure {
            mail to: 'team@example.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
         }
         changed {
            echo 'Things were different before...'
         }
    }

}







