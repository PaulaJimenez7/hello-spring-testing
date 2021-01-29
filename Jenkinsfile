#!/usr/bin/env groovy
pipeline {
    agent any
    
    options {
        ansiColor('xterm')
    }

    stages {
        stage('build') {
            steps {
                sh './gradlew assemble'
            }
        }
        stage('test') {
            steps {
                sh './gradlew  test'
            }
        }
    }
}
