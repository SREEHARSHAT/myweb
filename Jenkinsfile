@Library('myweb-libs')_
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
                TomcatDeploy('tomcat','ec2-user','172.31.9.194')
              

                
        }
            }
        }
    }
