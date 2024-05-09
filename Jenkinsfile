pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Compile your code
                sh 'javac -d target/classes src/*.java'
                
                // Package your code into a JAR file
                sh 'jar cvf myapp.jar -C target/classes .'
            }
        }

        stage('Unit Test') {
            steps {
                // Run your unit tests
                sh 'java -cp target/classes org.junit.runner.JUnitCore YourUnitTestClassName'
            }
        }

        stage('Integration Test') {
            steps {
                // Run your integration tests
                // Example: sh 'java -jar your_integration_test.jar'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your application
                // Example: sh 'scp myapp.jar user@host:/path/to/deployment/directory'
            }
        }
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

