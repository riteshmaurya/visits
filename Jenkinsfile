#!/usr/bin/env groovy
pipeline {
    environment {
    registry = "riteshmaurya/visits"
    registryCredential = ‘dockerhub’
  }
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
        stage('Upload to docker'){
                // tag = VersionNumber(versionNumberString: '${BUILD_DATE_FORMATTED, "yyyyMMdd"}.${BUILDS_TODAY}')
           steps{

                sh "docker build -t riteshmaurya/visits:${BUILD_NUMBER} ."
                // sh "docker tag riteshmaurya/visits:${BUILD_NUMBER} riteshmaurya/visits:"

                sh "docker push riteshmaurya/visits:latest" 
            }
     
        }
    }
}