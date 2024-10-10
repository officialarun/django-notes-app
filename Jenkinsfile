@Library("Shared") _
pipeline{
    agent {label "vinod"}
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/officialarun/django-notes-app.git","main")
                }
                
            }
            
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","dockerhub0600")
                }
                // echo "this is building the code"
                // sh "whoami"
                // sh "docker build -t notes-app:latest ."
            }
            
            
        }
        stage("Push to Docker Hub"){
            steps{
                script{
                    docker_push("notes-app","latest","dockerhub0600")
                }
            }
            
        }
        stage("Deploy"){
            steps{
                 echo "this is deploying the code"
                //  sh "docker run -d -p 8000:8000 notes-app:latest"
                sh "docker compose down && docker compose up -d"
            }
       
            
        }
    }
}
