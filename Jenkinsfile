pipeline {
	agent any
	    stages {
	        stage('Clone Repository') {
	        /* Cloning the repository to our workspace */
	        steps {
	        checkout scm
	        }
	   }
	   stage('Build Image') {
	        steps {
                sh 'docker build -t mymodel:v1 --build-arg http_proxy=http://fgt.halykbank.nb:8080 --build-arg https_proxy=https://fgt.halykbank.nb:8080 --file=Dockerfile --rm=true .'
	        }
	   }
	   stage('Run Image') {
	        steps {
		sh 'docker run -d -p 5000:4000 --name nlpmodel mymodel:v1'
	        }
	   }
	   stage('Testing'){
	        steps {
	            echo 'Testing..'
	            }
	   }
    }
}
