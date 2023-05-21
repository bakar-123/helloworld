pipeline {
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.9.1/bin:$PATH"
    }

    stages {
        stage('pulling code work') {
            steps {
               git branch: 'main', url: 'https://github.com/bakar-123/helloworld.git'
            }
        }
        stage('simple testing to display during builds') {
            steps {
               sh 'mvn clean compile'
            }
        }
        stage('maven building work') {
            steps {
               sh 'mvn clean install'
            }
        }
        stage('ssh credentials') {
            steps {
               sshagent(['pem_credentials']) {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.9.37:/opt/tomcat/webapps"
}
            }
        }
    }
}
