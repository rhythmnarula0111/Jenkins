pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build the code using a build automation tool (e.g., Maven)
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
                
                // Run integration tests
                sh 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool (e.g., SonarQube) to analyze the code
                sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                // Perform a security scan on the code using a tool (e.g., OWASP Dependency-Check)
                sh 'dependency-check --scan . --format HTML'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                sh 'ssh user@staging-server "deploy.sh"'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                sh 'ssh user@staging-server "run-tests.sh"'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                sh 'ssh user@production-server "deploy.sh"'
            }
        }
    }

    post {
        success {
            // Send email notification for successful pipeline execution
            emailext (
                subject: "Pipeline Success",
                body: "Your pipeline ran successfully.",
                to: "your@email.com"
            )
        }
        failure {
            // Send email notification for failed pipeline execution
            emailext (
                subject: "Pipeline Failed",
                body: "Your pipeline failed. Check the attached logs for details.",
                to: "your@email.com",
                attachLog: true
            )
        }
    }
}

