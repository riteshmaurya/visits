#!/usr/bin/env groovy
pipeline {
    environment {
    registry = "riteshmaurya/visits"
    registryCredential = 'dockerhub'
  }
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
        stage('Upload to docker'){
            steps{
            withDockerRegistry([credentialsId: "dockerhub", url: ""]){
                sh "docker build -t riteshmaurya/visits:${BUILD_NUMBER} ."

                sh "docker push riteshmaurya/visits:latest" 
            } 
            }
    
        }
    }
}