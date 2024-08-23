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
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Build stage completed successfully\n"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'Simulating: mvn test'
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Unit and Integration Tests completed successfully\n"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                echo 'Simulating: sonar-scanner analysis'
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Code Analysis completed successfully\n"
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'Simulating: security scan with OWASP Dependency Check'
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Security Scan completed successfully\n"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                echo 'Simulating: deployment to AWS EC2 (staging)'
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Deploy to Staging completed successfully\n"
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                echo 'Simulating: integration tests on staging server'
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Integration Tests on Staging completed successfully\n"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                echo 'Simulating: deployment to AWS EC2 (production)'
                script {
                    def logContent = readFile(file: "${env.LOG_FILE}") // Read existing content
                    writeFile file: "${env.LOG_FILE}", text: logContent + "Deploy to Production completed successfully\n"
                }
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
                attachLog: true
        }
    }
}
