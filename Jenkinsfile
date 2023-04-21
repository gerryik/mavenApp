pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{

        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkinsacct', url: 'https://github.com/gerryik/mavenApp.git']])
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
      sh 'mvn clean package sonar:sonar \
        -Dsonar.projectKey=sonarqTest \
        -Dsonar.projectName="sonarqTest" \
        -Dsonar.host.url=http://192.168.56.11:9000 \
        -Dsonar.token=sqp_7995a5b14b0cfe05c55e1cec033385fa45b6976c'
      }
    }
  }
}  
