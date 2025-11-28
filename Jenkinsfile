pipeline {
    agent any

    tools {
        maven 'mvn'   // <-- This must match the Maven name in Jenkins settings
    }

    stages {

        stage('checkout the code from github') {
            steps {
                git url: 'https://github.com/nikhil17-ng/pro3.git'
                echo 'github url checkout'
            }
        }

        stage('codecompile with akshat') {
            steps {
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }

        stage('codetesting with akshat') {
            steps {
                sh 'mvn test'
            }
        }

        stage('qa with akshat') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('package with akshat') {
            steps {
                sh 'mvn package'
            }
        }

        stage('run dockerfile') {
            steps {
                sh 'docker build -t myimg .'
            }
        }

        stage('port expose') {
            steps {
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }
    }
}
