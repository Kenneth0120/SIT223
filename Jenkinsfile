pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Fetching source code from GitHub...'
                // Normally, you'd use: checkout scm
            }
        }

        stage('Tool Install') {
            steps {
                echo 'Installing necessary build tools...'
                // This is where Maven or other tools would be installed if needed
            }
        }

        stage('Build') {
            steps {
                echo 'Building the code...'
                // Simulate the build process
                echo 'Simulating: mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Simulate unit and integration testing
                echo 'Simulating: mvn test'
            }
            post {
                success {
                    mail to: 'wowjaa1025@gmail.com',
                        subject: "Pipeline - Unit and Integration Tests SUCCESS: ${currentBuild.fullDisplayName}",
                        body: "The unit and integration tests completed successfully. Check the console output at ${env.BUILD_URL} for details."
                }
                failure {
                    mail to: 'wowjaa1025@gmail.com',
                        subject: "Pipeline - Unit and Integration Tests FAILURE: ${currentBuild.fullDisplayName}",
                        body: "The unit and integration tests failed. Check the console output at ${env.BUILD_URL} for details."
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                // Simulate code analysis (e.g., with SonarQube)
                echo 'Simulating: sonar-scanner analysis'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Simulate security scan using OWASP Dependency Check or similar tool
                echo 'Simulating: security scan with OWASP Dependency Check'
            }
            post {
                success {
                    mail to: 'wowjaa1025@gmail.com',
                        subject: "Pipeline - Security Scan SUCCESS: ${currentBuild.fullDisplayName}",
                        body: "The security scan completed successfully. Check the console output at ${env.BUILD_URL} for details."
                }
                failure {
                    mail to: 'wowjaa1025@gmail.com',
                        subject: "Pipeline - Security Scan FAILURE: ${currentBuild.fullDisplayName}",
                        body: "The security scan failed. Check the console output at ${env.BUILD_URL} for details."
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Simulate deployment to staging server
                echo 'Simulating: deployment to AWS EC2 (staging)'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                // Simulate integration testing on staging
                echo 'Simulating: integration tests on staging server'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Simulate production deployment
                echo 'Simulating: deployment to AWS EC2 (production)'
            }
        }
    }

    post {
        always {
            echo 'Sending final email notification...'
            mail to: 'wowjaa1025@gmail.com',
                subject: "Pipeline finished: ${currentBuild.fullDisplayName}",
                body: "Check console output at ${env.BUILD_URL}"
        }
    }
}
