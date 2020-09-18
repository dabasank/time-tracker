#!/usr/bin/env groovy

@Library('Shared-Libraries')_

pipeline {
    agent {label 'Java'}
    stages {
        stage("Git Checkout") {
            steps {
                git "https://github.com/dabasank/time-tracker.git"
            }
        }
        stage("Parallel Stage") {
            when {
                branch 'master'
            }
            failFast true
            parallel {
                stage("Dummy Stage") {
                    steps {
                        echo "Output of a Parallel Stage step"
                    }
                }
                stage("Build the Code"){
                    steps {
                        sh "mvn clean package"
                     }
                }
            }
        stage('Test'){
            steps {
                sh 'make check'
                junit 'reports/**/*.xml' 
            }
            post {
            failure{
                echo 'JUnit Test has Failed'
            }
        }
        }
      //stage("Deploying to TOMCAT Server"){
        //  steps{
         //     sshagent(['deply_user'])
         //     sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.12.143.198:/opt/apache-tomcat-8.5.55/webapp"
        //  }
     // }
        stage("Check-Deployment Logs"){
            steps{
                checkErrors ('[ERROR]', 0)
            }
        }      
    }
}
}
