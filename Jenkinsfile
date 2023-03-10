pipeline {
    agent any

    stages {
        stage('Checkout GIT') {
            steps {
                echo 'Pulling... ';
                    git branch: 'main',
                        url : 'https://github.com/olfaBenafia/DevOPs',
                        credentialsId: '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';
            }
        }

    }
}
