pipeline {
    agent any
    stages {
        stage('install-pip-deps') {
            steps {
                echo 'Installing all required dependencies...'
            }
        }

        stage('deploy-to-dev') {
            steps {
            echo 'Deploying to DEV environment...'
            }
        }

        stage('tests-on-dev') {
            steps {
            echo 'Running tests on DEV environment...'
            }
        }

        stage('deploy-to-stg') {
            steps {
            echo 'Deploying to STG environment...'
            }
        }

        stage('tests-on-stg') {
            steps {
            echo 'Running tests on STG environment...'
            }
        }

        stage('deploy-to-preprod') {
            steps {
            echo 'Deploying to PREPROD environment...'
            }
        }

        stage('tests-on-preprod') {
            steps {
            echo 'Running tests on PREPROD environment...'
            }
        }

        stage('deploy-to-prod') {
            steps {
            echo 'Deploying to PROD environment...'
            }
        }

        stage('tests-on-prod') {
            steps {
            echo 'Running tests on PROD environment...'
            }
        } 
    }
}
