pipeline {
    agent any

    environment {
        LOG_FILE = 'pipeline-log.txt' // Define the log file to be used
    }

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

                // Log the build status
                writeFile file: "${env.LOG_FILE}", text: "Build completed successfully\n"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Simulate unit and integration testing
                echo 'Simulating: mvn test'

                // Append the test results to the log
                writeFile file: "${env.LOG_FILE}", text: "Unit and Integration Tests completed successfully\n", append: true
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                // Simulate code analysis (e.g., with SonarQube)
                echo 'Simulating: sonar-scanner analysis'

                // Append the code analysis results to the log
                writeFile file: "${env.LOG_FILE}", text: "Code Analysis completed successfully\n", append: true
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Simulate security scan using OWASP Dependency Check or similar tool
                echo 'Simulating: security scan with OWASP Dependency Check'

                // Append the security scan results to the log
                writeFile file: "${env.LOG_FILE}", text: "Security Scan completed successfully\n", append: true
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Simulate deployment to staging server
                echo 'Simulating: deployment to AWS EC2 (staging)'

                // Append the deployment results to the log
                writeFile file: "${env.LOG_FILE}", text: "Deploy to Staging completed successfully\n", append: true
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                // Simulate integration testing on staging
                echo 'Simulating: integration tests on staging server'

                // Append the integration test results to the log
                writeFile file: "${env.LOG_FILE}", text: "Integration Tests on Staging completed successfully\n", append: true
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Simulate production deployment
                echo 'Simulating: deployment to AWS EC2 (production)'

                // Append the production deployment results to the log
                writeFile file: "${env.LOG_FILE}", text: "Deploy to Production completed successfully\n", append: true
            }
        }
    }

    post {
        always {
            echo 'Archiving logs...'
            archiveArtifacts artifacts: "${env.LOG_FILE}", allowEmptyArchive: true

            echo 'Sending final email with logs...'
            script {
                def logContent = readFile(file: "${env.LOG_FILE}")
                mail to: 'wowjaa1025@gmail.com',
                    subject: "Pipeline Status: ${currentBuild.currentResult}",
                    body: """Pipeline finished with status: ${currentBuild.currentResult}.
                    Please find the logs attached.""",
                    attachmentsPattern: "${env.LOG_FILE}" // Attach the log file
            }
        }
    }
}
