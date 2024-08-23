pipeline {
    agent any

    environment {
        LOG_FILE = "pipeline-log.txt"
    }

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Fetching source code from GitHub...'
            }
        }

        stage('Tool Install') {
            steps {
                echo 'Installing necessary build tools...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the code...'
                echo 'Simulating: mvn clean install'
                writeFile file: "${env.LOG_FILE}", text: "Build stage completed successfully\n", append: true
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'Simulating: mvn test'
                writeFile file: "${env.LOG_FILE}", text: "Unit and Integration Tests completed successfully\n", append: true
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                echo 'Simulating: sonar-scanner analysis'
                writeFile file: "${env.LOG_FILE}", text: "Code Analysis completed successfully\n", append: true
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'Simulating: security scan with OWASP Dependency Check'
                writeFile file: "${env.LOG_FILE}", text: "Security Scan completed successfully\n", append: true
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                echo 'Simulating: deployment to AWS EC2 (staging)'
                writeFile file: "${env.LOG_FILE}", text: "Deploy to Staging completed successfully\n", append: true
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                echo 'Simulating: integration tests on staging server'
                writeFile file: "${env.LOG_FILE}", text: "Integration Tests on Staging completed successfully\n", append: true
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                echo 'Simulating: deployment to AWS EC2 (production)'
                writeFile file: "${env.LOG_FILE}", text: "Deploy to Production completed successfully\n", append: true
            }
        }
    }

    post {
        always {
            echo 'Archiving logs...'
            archiveArtifacts artifacts: "${env.LOG_FILE}", allowEmptyArchive: true

            echo 'Sending final email with logs...'
            mail to: 'wowjaa1025@gmail.com',
                subject: "Pipeline Status: ${currentBuild.currentResult}",
                body: """Pipeline finished with status: ${currentBuild.currentResult}.
                Please find the attached logs for the pipeline.""",
                attachmentsPattern: "${env.LOG_FILE}"
        }
    }
}
