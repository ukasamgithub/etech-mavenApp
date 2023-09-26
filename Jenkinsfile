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
<<<<<<< HEAD
  -Dsonar.host.url=http://ec2-100-25-21-120.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_58c65334cdcfc9a8312b9216030e4e0648604'
=======
  -Dsonar.host.url=http://ec2-100-25-21-120.us-east-2.compute.amazonaws.com:9000 \
  -Dsonar.login=sqp_58c65334663cdcfc9a8312b9126030e4e0648604'
>>>>>>> ae0a081 (updated change)
      }
    }
  }
}
