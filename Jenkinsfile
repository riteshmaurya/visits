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
                tag = VersionNumber(versionNumberString: '${BUILD_DATE_FORMATTED, "yyyyMMdd"}.${BUILDS_TODAY}')

                sh "docker build -t riteshmaurya/visits:${BUILD_NUMBER} ."
                sh "docker tag riteshmaurya/visits:${BUILD_NUMBER} riteshmaurya/visits:"

                sh "docker push riteshmaurya/visits:${tag}" 
            }
     
        }
    }
}