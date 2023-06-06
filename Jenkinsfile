pipelines
    agent any

    stages {
        stage ('Build') {
            steps{

                git 'https://github.com/vj95sam/petadoption.git'

                sh "./mvnw compile"

                echo 'Building the Project with maven compile'
            }
        }
        stage ('Test') {
            steps{

                sh "./mvnw test"

                echo 'Testing the Project with maven test'
            }
        }
        stage ('Package') {
            steps{

                sh "./mvnw package"

                echo 'Packaging the Project with maven package'
            }
        }
        stage ('Containerize') {
            steps{

                sh "docker build -t pet-clinic-image ."

                echo 'Containerizing the App with Docker'
            }
        }
        stage ('Deploy') {
            steps{

                sh "docker run -d -p 9090:9090 pet-clinic-image"

                echo 'Deploy the App with Docker'
            }
        }
    }