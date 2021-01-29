#!/usr/bin/env groovy
pipeline {
    agent any
    
    options {
        ansiColor('xterm')
    }

    stages {
        stage('build') {
            steps {
                withGradle{
                    sh './gradlew assemble'
                } 
            }
        }
        stage('test') {
            steps {
                withGradle{
                    sh './gradlew  test'
                }              
            }
        }
    }
}
