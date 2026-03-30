pipeline {
    agent any

    stages {

        stage('Stage 1 - Hello Script') {
            steps {
                sh 'chmod +x scripts/stage1.sh && ./scripts/stage1.sh'
            }
        }

        stage('Stage 2 - Hello Script') {
            steps {
                sh 'chmod +x scripts/stage2.sh && ./scripts/stage2.sh'
            }
        }

    }
}
