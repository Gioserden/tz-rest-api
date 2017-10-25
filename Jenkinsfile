pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh'./gradlew clean assemble'
            }
        }
        stage('Test') {
            steps {
                sh'./gradlew clean check'
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'build/reports/tests/test/',
                    reportFiles: 'index.html',
                    reportName: 'Tests Report'
                ]
            }
        }
        stage('Deploy') {
            steps {
                sh'./gradlew clean shadowJar'
                sh './gradlew jacocoTestReport'
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'build/jacocoHtml/',
                    reportFiles: 'index.html',
                    reportName: 'Code Coverage Report'
                ]
            }
        }
    }
}