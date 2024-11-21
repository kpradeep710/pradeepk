pipeline{
   agent any
 environment {
       JAVA_HOME= 'C:/Program Files/Java/jdk-17'
       PATH = "${env.PATH};C:\\Program Files\\apache-maven-3.9.3-bin\\apache-maven-3.9.3\\bin"
    }
 stages {
        stage('clone repo') {
            steps {
                echo "Clone the Git repository"
                git clone: 'https://github.com/kpradeep710/maven-web-app.git'
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
                scp -i "/c/ProgramData/Jenkins/.jenkins/workspace/task-3@2/target/01-maven-web-app.war" ec2-user@13.201.90.156:/home/ec2-user
                '''
            }
        }
    }
}
