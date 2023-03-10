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
                        url : 'https://github.com/olfaBenafia/DevOPs',
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

    }
}
