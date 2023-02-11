pipeline {

  // Where to run stuff.
  agent any
  // What to run goes here
  environment {
    //Docker Hub Creds
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred')
  }
  stages {
    stage('build-sender') {
      steps {
        sh 'docker build -t suraj362/sender:${BUILD_ID} ./sender'
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        sh 'docker push suraj362/sender:${BUILD_ID}'

      }
     
    }
    stage('build-receiver') {
      steps {
        sh 'docker build -t suraj362/receiver:${BUILD_ID} ./receiver'
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        sh 'docker push suraj362/receiver:${BUILD_ID}'
        stash includes: "docker-compose.yml", name: "build"
      }

    }
    stage('deploy') {
      steps {
        unstash "build"
        sh 'build=${BUILD_ID} docker-compose up -d'

      }
      options {
        skipDefaultCheckout true
      }
      agent{
          label 'test-server'
      }

    }

  }

}
