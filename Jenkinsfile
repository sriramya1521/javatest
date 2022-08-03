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

        stage('proceed to Deploy'){
            steps {
                script {
                    if (env.BRANCH_NAME == "master") {
                        input('proceed for Deployment?')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}