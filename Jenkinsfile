pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 hemanth8877/paytm:movie'
            }
        }
       stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-hub') {
                     sh 'docker push hemanth8877/paytm:movie'
                  }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 shaikmustafa/paytm:movie'
            }
        }
    }
}
