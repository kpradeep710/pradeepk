pipeline {
  agent any
  environment {
      JAVA_HOME = "/usr/lib/jvm/java-17-openjdk" // Update this path
      PATH = "${JAVA_HOME}/bin:${env.PATH}"
      PATH = "/usr/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
           steps {
                git branch: 'main', credentialsId: '626473c6-9dfd-438c-885a-fb64492de479', url: 'https://github.com/kpradeep710/pradeepk.git'
            }
        }
       stage('Build') {
           steps {
              sh '/home/ec2-user/slavenode/tools/hudson.tasks.Maven_MavenInstallation/maven-3.9/bin/mvn clean package'  // Using Maven to build your application
            }
        }
        stage('Deploy') {
         steps {
              // Path to the PEM file and the deployment command
              sh '''
              scp -i C:/Documents/k.pradeepkumar.pem target/01-maven-web-app.war ec2-user@13.127.107.195:/home/ec2-user
              '''
            }
        }
    }
}
