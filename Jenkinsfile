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
    
    
