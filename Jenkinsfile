pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t springboot-cicd-demo:${BUILD_NUMBER} .'
            }
        }
    }
}
stage('Docker Build') {
    steps {
        sh 'docker version'
        sh 'docker build -t springboot-cicd-demo:${BUILD_NUMBER} .'
    }
}
