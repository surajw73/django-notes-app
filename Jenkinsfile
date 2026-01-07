@Library("shared") _
pipeline {
    agent {label "one"}

    stages {
        stage('hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage('code_clone') {
            steps {
                script{
                    clone("https://github.com/surajw73/django-notes-app.git","main")
                }
              }
            }
        stage('build') {
            steps {
                script{
                    docker_build("notes-app","latest","surajw73")
                }
              }
           }
           stage('push-to-docker') {
            steps {
                script{
                    docker_push("notes-app","latest","surajw73")
                }
               }
            }
            stage('deploy') {
            steps {
                sh "docker-compose up"
               }
            }
        
    }
}
