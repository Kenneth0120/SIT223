pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9' // Ensure this matches your Maven installation
    }

    environment {
        STAGING_SERVER = 'ec2-user@staging-server:/path/to/deploy'
        PRODUCTION_SERVER = 'ec2-user@production-server:/path/to/deploy'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Build the code using Maven
                bat 'mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Run unit and integration tests using Maven
                bat 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing Code...'
                // Run code analysis using SonarQube
                bat 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Perform security scan using OWASP Dependency Check
                bat 'dependency-check.bat --scan ./ --format XML --project MyProject'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to a staging server (adjust the path if necessary)
                bat 'scp target/my-app.war ${STAGING_SERVER}'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run integration tests on the staging server
                bat './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy to production server (adjust the path if necessary)
                bat 'scp target/my-app.war ${PRODUCTION_SERVER}'
            }
        }
    }

    post {
        always {
            echo 'Sending email notifications...'
            // Send email notification at the end of the pipeline
            mail to: 'developer@example.com',
                subject: "Pipeline finished: ${currentBuild.fullDisplayName}",
                body: "Check console output at ${env.BUILD_URL}"
        }
        failure {
            mail to: 'developer@example.com',
                subject: "Pipeline failed: ${currentBuild.fullDisplayName}",
                body: "Check console output at ${env.BUILD_URL}"
        }
    }
}
