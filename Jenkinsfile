pipeline {

    // Where to run stuff.
    agent any
    // What to run goes here.
    environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred')
	}
    stages {
        stage('build-sender') {
            steps {
                sh 'docker build -t suraj362/sender:${BUILD_ID} ./sender'
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push bharathirajatut/nodeapp:${BUILD_ID}'
                
        }
		agent {
			label 'test-server'
		}
        }
        stage('build-receiver') {
            steps {
                sh 'ls'
                
            }
            options{
                skipDefaultCheckout true
            }
            
        }
       
       
    }
        
       
}
