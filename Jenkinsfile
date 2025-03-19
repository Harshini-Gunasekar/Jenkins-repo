// pipeline {
//     agent any

//     environment {
//         IMAGE_NAME = "harshini794/my-app"
//         REGISTRY = "docker.io"
//         DOCKER_CREDENTIALS_ID = "harshini794"
//         GITHUB_CREDENTIALS_ID = "Harshini-Gunasekar"
//         APP_DIR = "/opt/docker-kec"
//     }

//     stages {
//         stage('Checkout Code') {
//             steps {
//                 git credentialsId: GITHUB_CREDENTIALS_ID, url: 'https://github.com/Harshini-Gunasekar/Jenkins-repo.git', branch: 'main'
//             }
//         }

//         stage('Build Docker Image') {
//             steps {
//                 script {
//                     sh "docker build -t $IMAGE_NAME:latest ."
//                 }
//             }
//         }

//         stage('Login to Docker Registry') {
//             steps {
//                 script {
//                     withCredentials([usernamePassword(credentialsId: DOCKER_CREDENTIALS_ID, usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
//                         sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
//                     }
//                 }
//             }
//         }

//         stage('Push Image to Docker Registry') {
//             steps {
//                 script {
//                     sh "docker push $IMAGE_NAME:latest"
//                 }
//             }
//         }

//         stage('Deploy using Docker Compose') {
//             steps {
//                 script {
//                     sh "docker-compose up -d"
//                 }
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Pipeline executed successfully! '
//         }
//         failure {
//             echo 'Pipeline failed! Check the logs for errors.'
//         }
//     }
// }
pipeline {
    agent any

    environment {
        IMAGE_NAME = "harshini794/my-app"
        REGISTRY = "docker.io"
        APP_DIR = "/home/vboxuser/jenkins/"
        DOCKER_USER = "harshini794""          // Replace with your Docker Hub username
        DOCKER_PASS = "Harshini@05"          // Replace with your Docker Hub password
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Harshini-Gunasekar/Jenkins-repo.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $IMAGE_NAME:latest ."
                }
            }
        }

        stage('Login to Docker Registry') {
            steps {
                script {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Image to Docker Registry') {
            steps {
                script {
                    sh "docker push $IMAGE_NAME:latest"
                }
            }
        }

        stage('Deploy using Docker Compose') {
            steps {
                script {
                    sh "docker-compose up -d"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed! Check the logs for errors.'
        }
    }
}
