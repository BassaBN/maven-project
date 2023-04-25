pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Deploy'){
            steps{
                sh 'mvn clean package'
                sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
    
}