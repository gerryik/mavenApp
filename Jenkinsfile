pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
       }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
      stage('unittest'){
        steps{
            sh 'mvn test'
        }
    }
    stage('sonarscanner'){
      steps{
      sh "mvn clean verify sonar:sonar \
  -Dsonar.projectKey=team5codereview \
  -Dsonar.projectName='team5codereview' \
  -Dsonar.host.url=http://ec2-107-22-47-64.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_0e5ca3fb66d661c1efd895d8370236860af9bfb6"
      }
    }
  }
}
