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
        stage("Build using Maven") {
            steps {
                sh "mvn clean package"
            }
        }
        //stage('Test'){
         //   steps {
         //       sh 'make check'
         //       junit 'reports/**/*.xml' 
         //   }
      //  }
      //stage("Deploying to TOMCAT Server"){
        //  steps{
         //     sshagent(['deply_user'])
         //     sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.12.143.198:/opt/apache-tomcat-8.5.55/webapp"
        //  }
     // }
        stage("Check-Deployment Logs"){
            steps{
                checkErrors ('WARNING', 10)
            }
        } 
     
      
    }
}
