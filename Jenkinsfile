pipeline {
    agent any

    stages {
        stage ("stage 1 - clone github code") {
            agent any
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'Dakshjain1', url: 'https://github.com/Dakshjain1/locus_task.git']]])
                sh 'cd locus_task'
                sh "ls"
            }
        }
       
    }
    post {
       
        success {
             mail body: "<b>Sample</b><br><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL of build: ${env.BUILD_URL}", charset: 'UTF-8', from: 'daksh.jain00@gmail.com', mimeType: 'text/html', replyTo: 'daksh.jain00@gmail.com', subject: "Success in CI: Project name -> ${env.JOB_NAME}", to: "daksh.jain00@gmail.com";
        }
        failure {
            mail body: "<b>Sample</b><br><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL of build: ${env.BUILD_URL}", charset: 'UTF-8', from: 'daksh.jain00@gmail.com', mimeType: 'text/html', replyTo: 'daksh.jain00@gmail.com', subject: "error in CI: Project name -> ${env.JOB_NAME}", to: "daksh.jain00@gmail.com";
        }
       
    }
}
