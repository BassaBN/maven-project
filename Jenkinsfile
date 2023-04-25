pipeline {
    agent any

    tools{
        maven 'maven'
    }

    parameters{
        string(name: 'tomcat_stg', defaultValue: '43.207.224.32', description: 'Staging Server')
        string(name: 'tomcat_prod', defaultValue: '52.198.219.87', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

     stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo '開始存檔...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

     stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        sh "scp -i /home/nick/KeyForJenkinsTomcat.pem **/target/*.war ec2-user@${params.stg}:/usr/share/tomcat/webapps"
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                        sh "scp -i /home/nick/KeyForJenkinsTomcat.pem **/target/*.war ec2-user@${params.tomcat_prod}:/usr/share/tomcat/webapps"
                    }
                }
            }
        }
    }
}