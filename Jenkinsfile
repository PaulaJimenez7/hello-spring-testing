#!/usr/bin/env groovy
pipeline {
    agent any
    
    options {
        ansiColor('xterm')
    }

    stages {
        stage("archive"){
            steps{
                withGradle{
                    withCredentials([string(credentialsId: 'gitLabPrivateToken',variable: 'TOKEN')]){
                        sh './gradlew publish'
                    }
                }
            }
        }

    }
}
