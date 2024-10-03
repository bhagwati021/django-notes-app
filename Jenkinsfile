@Library("Shared") _
pipeline{
    
    agent { label "agent-1"}
    
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
                clone("https://github.com/bhagwati021/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","Bhags021")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","Bhags021")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
