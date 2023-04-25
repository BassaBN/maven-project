pipeline {
    agent any
    tools{
        maven 'maven'
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo '开始存档....'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to staging'){
            steps{
                build job:'deploy-to-staging'
            }
        }

         stage ('Deploy to Production'){
            steps{
                build job: 'deploy-to-production'
            }
            post {
                success {
                    echo '代码成功部署到生产环境'
                }

                failure {
                    echo '部署失败'
                }
            }
        }




    }
}