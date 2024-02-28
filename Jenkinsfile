pipeline {
    agent any
    
    stages {
        
           stage('Preparation') {
            steps {
                // Clean the workspace before cloning
                deleteDir()
            }
        }
        
        stage('git clone ') {
            steps {
                sh 'git clone https://github.com/yosimi20/visualcode.git'
            }
        }
        
          stage('docker image') {
            steps {
                dir('visualcode') {
                    sh 'docker build -t flask-app .'
                }
            }
        }
        
        stage('image ps ') {
            steps {
                sh 'docker images'
            }
        }
        
        stage('Create and Run Container') {
            steps {
                // Assuming flask-app as image name and flask-container as container name
                // Change 5000:5000 if your app listens on a different port
                sh 'docker run -d -p 5000:5000 --name flask-jenkins-container flask-app'
            }
        }
        
          stage('Verify Container') {
            steps {
                sh 'docker ps -a'
            }
        }
    }

}
