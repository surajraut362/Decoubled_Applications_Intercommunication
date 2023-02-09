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
            options{
                skipDefaultCheckout true
            }
            steps {
                sh 'ls'
            }
            agent { 
                label 'test-server'
            }
        }
       
    }
        
       
}
