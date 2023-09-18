pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
       checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-id', url: 'https://github.com/ukasamgithub/etech-mavenApp.git']])
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
    stage('codequality'){
      steps{
        sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=etech-team4 \
  -Dsonar.projectName='etech-team4' \
  -Dsonar.host.url=http://ec2-3-83-160-155.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_73c90e4fd872e5faa1d7e9673c2b091f656e588d'
      }
    }
  }
}
