pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh'./gradlew clean assenble'
            }
        }
        stage('Test') {
            steps {
                sh'./gradlew clean check'
            }
        }
        stage('Deploy') {
            steps {
                sh'./gradlew clean shadowJar'
            }
        }
    }
}