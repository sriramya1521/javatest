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
                echo 'Testing..'
                echo "${env.BUILD_URL}"
            }
        }

        Stage('proceed to Deploy'){
            steps{
                script{
                if {env.BRANCH_NAME == "master"} {
                        input ('proceed for prod deployment?')
                       
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }


        }
    }

    post {
         always {
            echo 'One way or another, I have finished'
            
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







}