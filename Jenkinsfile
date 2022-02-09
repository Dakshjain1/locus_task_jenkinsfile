pipeline {
    agent any

    stages {
        stage ("stage 1 - clone github code") {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'Dakshjain1', url: 'https://github.com/Dakshjain1/locus_task.git']]])
                sh "ls"
                sh 'cat pom.xml'
            }
        }
         stage ("stage 2 - validate the code") {
            steps {
                sh "/maven/apache-maven-3.6.3/bin/mvn validate"
            }
        }
        stage ("stage 3 - compile the code") {
            steps {
                sh "/maven/apache-maven-3.6.3/bin/mvn compile"
            }
        }
        stage ("stage 4 - perform unit testing") {
            steps {
                sh "/maven/apache-maven-3.6.3/bin/mvn test"
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage ("stage 5 - prepare the package") {
            steps {
                sh "/maven/apache-maven-3.6.3/bin/mvn package"
            }
        }
        stage ("stage 6 - test the jar file") {
            steps {
                sh "java -jar targets/my-app-1.0-SNAPSHOT.jar"
            }
        }
       stage ("final stage - cleaning workspace") {
           steps {
               echo "can clean the workspace after job is done"
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
