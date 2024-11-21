pipeline {
  agent { label 'agent-node' }
    stages {
        stage('clone repo') {
            steps {
                echo "Clone the Git repository"
                git clone 'https://github.com/kpradeep710/maven-web-app.git'
            }
        }

        stage('Build') {
            steps {
                echo "build the maven project"
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                echo "connected to ec2-instance and ready to deploy"
                bat '''
                scp -i C:/Documents/k.pradeepkumar.pem target/01-maven-web-app.war ec2-user@13.201.90.156:/home/ec2-user
                '''
            }
        }
    }
}
