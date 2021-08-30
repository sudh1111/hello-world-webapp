pipeline {
    agent any

    tools{
        dockerTool 'docker'
    }

    stages {
        stage('Git Clone') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/sudh1111/hello-world-webapp.git'
            }
        }
        stage('Deploy') {
            steps {
               script {
                   // This step should not normally be used in your script. Consult the inline help for details.
                   withDockerRegistry(credentialsId: 'docker-hub-push-credentials', toolName: 'docker') {
                   // some block
                   def image = docker.build("kanishkajain30/hello-world:$BUILD_NUMBER")
                   image.push()
                   }
               }
            }
        }
    }
