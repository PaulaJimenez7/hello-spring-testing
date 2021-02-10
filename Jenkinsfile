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
                    withCredentials([usernamePassword(credentialsId: 'ApacheArchiva', passwordVariable: 'archivaPassword', usernameVariable: 'archivaUsername')]) {
                        sh './gradlew publish'
                    }
                }
            }
        }

    }
}
