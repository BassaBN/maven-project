pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Deploy'){
            steps{
                sh 'mvn clean package'
                sh "/usr/local/bin/docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
    
}