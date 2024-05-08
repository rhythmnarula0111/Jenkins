pipeline {
    agent any

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
                // Assuming your unit tests are executed using a command like 'mvn test'
                sh 'mvn test'

                // Run integration tests with Selenium or Postman
                // Assuming your integration tests are executed using a command like 'mvn verify'
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
