#!/usr/bin/env groovy
pipeline {
    environment {
    registry = "riteshmaurya/visits"
    registryCredential = 'dockerhub'
  }
  agent {
    dockerfile {
      args "-v /var/run/docker.sock:/var/run/docker.sock --privileged"
    }
    }    
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
                sh "ls -al /var/run/"
            }
        }
        stage('Upload to docker'){
            steps{
            withDockerRegistry([credentialsId: "dockerhub", url: ""]){
                sh "ls -al /var/run"
                sh "docker build -t riteshmaurya/visits:${BUILD_NUMBER} ."

                sh "docker push riteshmaurya/visits:latest" 
            } 
            }
    
        }
    }
}
