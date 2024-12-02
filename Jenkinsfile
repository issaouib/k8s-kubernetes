pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
            }
        }  
      stage('Unit Test - JUnit and Jacoco') {
            steps {
              //sh "export JAVA_HOME=/opt/openjdk17; mvn test"
              sh "mvn test"
            } 
            post {
              always {
                junit 'target/surefire-reports/*.xml'
                jacoco execPattern: 'target/jacoco.exec'
              }
            }         
      }
    }
}