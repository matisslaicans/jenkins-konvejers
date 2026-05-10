def build() {
    echo 'Installing all required dependencies...'
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    sh 'ls'
    sh 'python3 -m venv venv'
    sh './venv/bin/python -m pip install -r requirements.txt'
    echo "Dependencies successfully installed.."
}

def deploy(String environment, int port){
    echo "Deployment to ${environment} environment has started.."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    sh "pm2 delete greetings-app-${environment} || true"
    sh "pm2 start app.py --name greetings-app-${environment} --interpreter ./venv/bin/python -- --port ${port}"
    echo "Deployment to ${environment} environment finished.."
}

def test(String environment){
    echo "Testing greetings app on ${environment} environment has started.."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/course-js-api-framework'
    sh 'npm install'
    sh "npm run greetings greetings_${environment}"
    echo "Testing greetings app on ${environment} environment finished.."
}

pipeline {
    agent any
    stages {
        stage('install-pip-deps') {
            steps {
                script { build() }
            }
        }

        stage('deploy-to-dev') {
            steps {
                script { deploy('dev', 7001) }
            }
        }

        stage('tests-on-dev') {
            steps {
                script { test('dev') }
            }
        }

        stage('deploy-to-stg') {
            steps {
                script { deploy('stg', 7002) }
            }
        }

        stage('tests-on-stg') {
            steps {
                script { test('stg') }
            }
        }

        stage('deploy-to-preprod') {
            steps {
                script { deploy('preprod', 7003) }
            }
        }

        stage('tests-on-preprod') {
            steps {
                script { test('preprod') }
            }
        }

        stage('deploy-to-prod') {
            steps {
                script { deploy('prod', 7004) }
            }
        }

        stage('tests-on-prod') {
            steps {
                script { test('prod') }
            }
        } 
    }
}
