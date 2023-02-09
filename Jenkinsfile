pipeline {

    // Where to run stuff.
    agent any
    // What to run goes here.
    stages {
        stage('build-sender') {
            steps {
                sh 'ls'
        }
        }
        stage('build-receiver') {
            steps {
                sh 'ls'
            }
            agent { 
                label 'test-server'
            }
        }
       
    }
        
       
}
