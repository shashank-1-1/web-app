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
               // sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
                sshagent(['azure-jenkins-agent']) {
                    sh """
                        scp -o StrictHostKeyChecking=no target/*.war ec2-user@13.233.96.152: /opt/tomcat-10/webapps
                    
                        ssh ec2-user@13.233.96.152 /opt/tomcat-10/bin/shutdown.sh
                    
                        ssh ec2-user@13.233.96.152 /opt/tomcat-10/bin/startup.sh
               
                    """
            }

            }
        }
    }
}
