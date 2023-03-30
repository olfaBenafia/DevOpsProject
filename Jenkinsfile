pipeline {
    agent any
    
    environment {
    		DOCKERHUB_CREDENTIALS=credentials('docker_hub')
    		}

    stages {
        stage('Checkout GIT') {
            steps {
                echo 'Pulling... ';
                    git branch: 'main',
                        url : 'https://github.com/olfaBenafia/DevOpsProject.git',
                        credentialsId: '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';
            }
        }
        stage('Cleaning the project') {     
            steps {
                echo 'cleaning project ...'
                sh 'mvn clean package'
            }
        }
        
        stage('Compiling the artifact') {             
            steps {
                echo "compiling"
                sh 'mvn compile'
            }
        }
        stage ('Docker build') {
             steps {
            sh ' docker build -t olfabenafia/tpachatproject-1.0:latest .'
            }
        }
        stage ('Docker login'){
        	steps {
        	sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
        	}
        }
        stage ('Docker push'){
        	steps {
        	sh 'docker push olfabenafia/tpachatproject-1.0:latest'
        	}
        }
        stage ('Docker logout'){
        	steps {
        	sh 'docker logout'
        	}
        }
        
      }

    
    
}
