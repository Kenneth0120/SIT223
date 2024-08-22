pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Example: Use Maven to build
                bat 'mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Example: Use JUnit for testing
                bat 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing Code...'
                // Example: Use SonarQube for code analysis
                bat 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Example: Use OWASP Dependency Check
                bat 'dependency-check --scan .'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Example: Deploy to AWS EC2 instance
                bat 'scp target/my-app.war ec2-user@staging-server:/path/to/deploy'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Example: Run integration tests on staging
                bat './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Example: Deploy to AWS EC2 instance
                bat 'scp target/my-app.war ec2-user@production-server:/path/to/deploy'
            }
        }
    }

    post {
        always {
            mail to: 'developer@example.com',
                subject: "Pipeline finished: ${currentBuild.fullDisplayName}",
                body: "Check console output at ${env.BUILD_URL}"
        }
    }
}
