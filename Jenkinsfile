@Library("shared") _
pipeline{
    
    agent{ label "rayeez" }
    
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
                    clone("https://github.com/iam-rayees/django-notes-app.git","main")
                }
            }
        }
    
        stage("Build"){
            steps{
                script{
                    docker_biuld("notes-todo-app","latest","rayeez")
                }
            }
        }
    
        stage("Test"){
            steps{
                echo "This is Testing the code"
            }
        }
    
        stage("Push"){
            steps{
                script{
                    docker_push("notes-todo-app","latest","rayeez")
                }
            }
        }
        
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
