@Library("SharedLib") _
pipeline{
    agent {label 'vinod'}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code'){
            steps{
                script{
                    gitclone("https://github.com/aryanrangapur/django-notes-app.git", "main")
                }
               
            }
        }
        stage('Build'){
            steps{
                script{
                    docker_build("notes-app","latest","aryanrangapur")
                }
            }
        }
        stage('Push to DockerHub'){
            steps{
                echo "Pushing image to DockerHub"
                script{
                    docker_push("notes-app","latest","aryanrangapur")
                }
            }
        }
        stage('Deploy'){
            steps{
                echo "Deploying Here"
                sh "docker compose up -d"
            }
        }
    }
}
