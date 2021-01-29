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
            post{
                success{
                    archiveArtifacts 'build/libs/*.jar'
                }
            }
        }
        stage('test') {
            steps {
                withGradle{
                    sh './gradlew clean test'
                }              
            }
            post{
                always{
                    junit 'buils/test-results/test/TEST-*.xml'
                }
            }
        }
    }
}
