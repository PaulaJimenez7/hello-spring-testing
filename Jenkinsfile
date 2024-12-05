#!/usr/bin/env groovy
pipeline {
    agent any
    
    options {
        ansiColor('xterm')
    }

    stages {
        stage("nexus"){
            steps{
                withGradle{
                   withCredentials([usernamePassword(credentialsId: 'ApacheArchiva', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh './gradlew publish'
                    }
                }
            }
        }

    }
}
