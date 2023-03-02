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
        ///stage("deploy-dev"){
                ///sshagent(['azure-jenkins-agent']) {
	                ///sh "mv target/myweb*.war target/myweb11.war"
		
		           ///         sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.9.7:/opt/tomcat8/webapps/"
		
		             ///       sh "ssh ec2-user@172.31.9.7 /opt/tomcat8/bin/startup.sh"
        ///    }
       }
	    
    }


