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
                    junit 'build/test-results/test/TEST-*.xml'
                    //jacoco(execPattern: 'build/jacoco/test.exec')
                }
            }
        }
        stage('pitest'){
            steps{
                withGradle{
                    sh './gradlew clean pitest'
                }
            }
            post{
                always{
                    pitmutation mutationStatsFile: 'build/reports/pitest/**/mutations.xml'
                }
            }
        }
    }
}
