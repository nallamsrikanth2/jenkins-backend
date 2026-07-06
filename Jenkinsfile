pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    environment {
        def appversion = ''
    }
    stages {
        stage('read the package version') {
            steps {
                script {
                    def packagejson = readJSON file: 'package.json'
                    appversion = packagejson.version
                    echo "application app version = ${appversion}"
                }
            }
        }
        stage ( 'build') {
            steps {
                sh """
                    npm install
                    ls -ltr
                """
            }
        }
        stage( 'deploy') {
            steps {
                sh """
                    zip -r -q backend-${appversion}.zip * -x Jenkinsfile -x backend-${appversion}.zip
                    ls -ltr
    
                """
            }
        }
    }
}