pipeline {
    agent any

    tools {
        maven 'Maven' // This assumes you have configured Maven in Jenkins under Manage Jenkins > Global Tool Configuration
    }

    stages {
        stage('Build') {
            steps {
                // Use Maven to build the code
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests with JUnit
                sh 'mvn test'

                // Run integration tests with Selenium or Postman
                sh 'mvn verify'
            }
        }
        // Define other stages similarly
    }

    post {
        success {
            // Send success notification email
            emailext (
                subject: "Pipeline Success",
                body: "Your pipeline ran successfully.",
                to: "rhythmn00@gmail.com"
            )
        }
        failure {
            // Send failure notification email with logs attached
            emailext (
                subject: "Pipeline Failed",
                body: "Your pipeline failed. Check the attached logs for details.",
                to: "rhythmn00@gmail.com",
                attachLog: true
            )
        }
    }
}
