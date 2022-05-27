pipeline {
    agent any
    environment {
        PATH = "/opt/mavens/bin/:$PATH"
    }
    stages {
        stage("git clone"){
            steps{
                git branch: 'dev', url: 'https://github.com/kajamal/maven-webapp.git' 
            }
            
        }
        stage("build code"){
            steps{
                sh "mvn clean install"
            }
            
        }

        stage("deploy"){
            steps{
                sshagent(['deploy']) {
                  sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline_job2/target/demo.war ubuntu@3.85.92.62:/home/ubuntu/apache-tomcat-8.5.79/webapps"
                }
                
            }
              
        }
    }
    
}


