pipeline {

    // Where to run stuff.
    agent any
    // What to run goes here.
    stages {
        stage('build-sender') {
            steps {
                sh 'ls'
                stash includes: 'docker-compose.yml', name: 'script'
        }
        }
        stage('build-receiver') {
            options{
                skipDefaultCheckout true
            }
            steps {
                unstash 'script'
                sh 'ls'
            }
            agent { 
                label 'test-server'
            }
        }
       
    }
        
       
}
