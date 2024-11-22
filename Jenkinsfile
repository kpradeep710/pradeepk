pipeline {
  agent { label 'agent-node' }
  environment {
      PATH = "C:\\Program Files\\Git\\bin;${env.PATH}"
    }
    stages {
        stage('Checkout') {
           steps {
                git branch: 'main', credentialsId: '626473c6-9dfd-438c-885a-fb64492de479', url: 'https://github.com/kpradeep710/pradeepk.git'
            }
        }
       stage('Build') {
           steps {
              bat 'mvn clean package'  // Using Maven to build your application
            }
        }
        stage('Deploy') {
         steps {
              // Path to the PEM file and the deployment command
              bat '''
              scp -i C:/Documents/k.pradeepkumar.pem target/01-maven-web-app.war ec2-user@13.127.107.195:/home/ec2-user
              '''
            }
        }
    }
}
