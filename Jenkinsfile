pipeline{
    agent any
    tools{
        maven 'Maven3'
    }
    stages{
        stage("GIT PUll"){
            steps{
                git 'https://github.com/SREEHARSHAT/myweb'
            }
        }
        stage("Maven Build"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("Deploy to Tomcat"){
            steps{
                sshagent(['tomcat']) {
                sh "mv target/*war target/myweb.war"
                sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.9.194:/opt/tomcat8/webapps"
                sh "ssh ec2-user@172.31.9.194 /opt/tomcat8/bin/shutdown.sh"
                sh "ssh ec2-user@172.31.9.194 /opt/tomcat8/bin/startup.sh"

                
        }
            }
        }
    }
}
