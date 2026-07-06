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
    }
}