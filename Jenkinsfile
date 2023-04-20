pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
      }
    }
  }
  stages {
    stage('Build the Java Maven Applcation') {
      steps {
      
        sh 'mvn -B -DskipTests clean package'
        sh 'echo "Built the Maven Application"'
      }
    }
    stage('Test the Java Maven Application') {
      steps {
        sh 'mvn test'
        sh 'echo "Tested the Java Maven Applcation"'
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
      }
      stage('Deliver') {
        steps {
          sh 'java -jar target/my-app-1.0-SNAPSHOT.jar'
          sh 'Successful!'
        }
      }
}
   
      
