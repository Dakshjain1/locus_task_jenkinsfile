pipeline {
    agent any
    
    stages {
        stage ("stage 1 ") {
            agent any
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'Dakshjain1', url: 'https://github.com/Dakshjain1/locus_task_jenkinsfile.git']]])
                sh "ls*"
            }
        }
        // stage ("stage 1 ") {
        //     agent any
        //     steps {
        //         echo "1"
        //     }
        // }
        // stage ("stage 1 ") {
        //     agent any
        //     steps {
        //         echo "1"
        //     }
        // }
        // stage ("stage 1 ") {
        //     agent any
        //     steps {
        //         echo "1"
        //     }
        // }
    }
    post {
        
    }
}
