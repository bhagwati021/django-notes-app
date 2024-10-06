@Library("shared") _
pipeline {
    agent { label "agent-1" }

    stages {
         stage('hello') {
            steps {
                script{
                    hello()
                }
            }
         }
        
        stage('clone') {
            steps {
                script{
                    clone("https://github.com/bhagwati021/django-notes-app.git","main")
                }
            }
        }
        
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest","bhags021")
                    
                }
            }
        }
        
        stage('Test') {
            steps {
                echo "this is testing the code/app"
                
            }
        }
        
        stage('push to dockerhub') {
            steps {
              script{
                  docker_push("notes-app","latest","bhags021")
              }
              
            }
        }
        
        stage('Deploy') {
            steps {
                echo "this is deploying the code/app"
                sh "docker compose down && docker compose up -d"
            }
        }
        
    }
}
