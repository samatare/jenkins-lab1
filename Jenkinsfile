pipeline {
    agent any
    environment {
        IMAGE = "samatare/jenkins-lab-nit-khadija:yasmin"
    }
    stages {
        stage('Build') {
            steps {
              sh 'docker build -t samatare/jenkins-lab-nit-khadija:yasmin .'
            }
        }
        stage('login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'docker-hub',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }
        stage('push') {
            steps {
                sh 'docker push samatare/jenkins-lab-nit-khadija:yasmin'
            }
        }
        stage('deploy') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flask-container $IMAGE'
            }
        }
    }
}
