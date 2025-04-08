pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub') // Replace with your actual Jenkins credential ID
        IMAGE_NAME = 'faisalkhan158/portfolio'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
        git branch: 'main', url: 'https://github.com/faisalkhan158/DevOps-Task2.git'
           }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'CI=false npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh """
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                        docker push $IMAGE_NAME
                    """
                }
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 80:80 --name react-app $IMAGE_NAME'
            }
        }
    }
}
