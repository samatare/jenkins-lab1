pipeline {
    agent any
environment {
    IMAGE = "samatare/jenkins-lab-nit-khadija:yasmin"
}
    stages {
 stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/samatare/jenkins-lab1.git',
                  
            }
        }

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

        stage('deplouy') {
        
            steps {
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true

                docker run -d \
                  -p 5000:5000 \
                  --name flask-container \
                  $IMAGE
                '''
            }

                
            }
        }
    }
}
