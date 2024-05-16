pipeline {
    agent any
        tools {
            jdk 'java-21-corretto'
        }
      
    stages {
        stage('Start') {
            steps {
                echo 'welcome to the build'
                sh 'whoami'
                sh 'ls ~/'
                sh 'ls ~/.ssh'
            }
        }
        stage('Checkout') {
            steps {
                echo 'checkout'
                step([$class: 'WsCleanup'])
                git branch: 'develocity-1',
                    credentialsId: 'github',
                    changelog: true,
                    url: 'git@github.com:marcoman/ofbiz-framework.git'
            }
        }
        stage('Build') {
            steps {
                echo './gradlew cleanAll loadAll test'
                sh './gradlew cleanAll loadAll test'
            }
        }
    }
}