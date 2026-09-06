@Library("Shared") _

pipeline {
    agent { label "vinod" }

    stages {
        stage("Hello"){
            steps {
                script{
                    hello()
                }
            }
        }

        stage("Code") {
            steps {
                script {
                    clone('https://github.com/hritikranjan1/django-notes-app.git',"main")
                }
            }
        }

        stage("Build") {
            steps {
                script{
                docker_build("notes_app","latest" , "hritikranjan1")
                }
            }
        }

        stage("Push Images to Docker Hub") {
            steps {
                script{
                    docker_push("notes-app","latest","hritikranjan1")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying the application..."

                sh "docker compose up -d"
            }
        }
    }
}
