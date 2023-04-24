pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn package'
            }
            post {
                success {
                    echo '开始存档...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
