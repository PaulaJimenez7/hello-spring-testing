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
        /*stage('test') {
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
                always{*/
                    //pitmutation mutationStatsFile: 'build/reports/pitest/**/mutations.xml'
                /*}
            }
        }

        stage('pmdtest'){
            steps{
                withGradle{
                    sh './gradlew check'
                }
            }
            post{
                always{
                    recordIssues(
                        enabledForFailure: true, 
                        tools: [java(), pmdParser(pattern: 'build/reports/pmd/*.xml'),spotBugs(pattern: 'build/reports/spotbugs/*.xml')]
                    )

                }
            }
        }
        stage('sonarQube') {
            steps { 
                configFileProvider([configFile(fileId: 'hello-spring-testing-gradle.properties', targetLocation: 'gradle.properties')]) {
                    withGradle{
                        withSonarQubeEnv(credentialsId:'9a7e16ef-5513-440a-b2f1-09233ae2e79e', installationName: 'local') { 
                            sh './gradlew sonarqube'
                        }
                    }
                }              
            }
        }*/
        stage("owasp"){
            steps{
                sh './gradlew dependencyCheckAnalyze'
            }
            post{
                always{
                   
                }
            }
        }

    }
}
