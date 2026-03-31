pipeline {
    agent any

     parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'staging', 'production'],
            description: 'Select deployment environment'
        )
    }

    stages {

        stage('Build') {
            steps {
                echo "Building application..."
            }
        }

        stage('Deploy to Dev') {
            when {
                expression { params.ENVIRONMENT == 'dev' }
            }
            steps {
                echo "Deploying to DEV environment"
            }
        }

    }
}
