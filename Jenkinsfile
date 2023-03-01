pipeline{
    agent any
    
    environment{
        PATH = "/usr/share/maven/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/shashank-1-1/web-app.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                //sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
                sshagent(['azure-jenkins-agent']) {
                    sh """
                        scp -o StrictHostKeyChecking=no target/myweb.war ec2@13.127.148.236:/opt/tomcat-10/webapps
                    
                        ssh ec213.127.148.236 /opt/tomcat-10/bin/shutdown.sh
                    
                        ssh ec213.127.148.236 /opt/tomcat-10/bin/startup.sh
               
                    """
            }

            }
        }
    }
}
