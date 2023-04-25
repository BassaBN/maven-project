pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Deploy'){
            steps{
                sh 'mvn clean package'
            }
        }
    }
    
}