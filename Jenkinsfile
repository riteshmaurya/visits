#!/usr/bin/env groovy
pipeline {
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
        stage('Upload to docker'){
            steps{
                sh "docker build -t riteshmaurya/visits:${BUILD_NUMBER} ."
                ah "docker tag riteshmaurya/visits:${BUILD_NUMBER} riteshmaurya/visits:latest"

                sh "docker push riteshmaurya/visits:${tag}" 
            }
     
        }
    }
}