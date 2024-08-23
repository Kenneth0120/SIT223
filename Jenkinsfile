pipeline {
    agent any 

    environment {
        DIRECTORY_PATH = '/Users/pauleccarius/Library/CloudStorage/OneDrive-DeakinUniversity/SIT223 Professional Practice in Information Technology/5.1P/' 
        TESTING_ENVIRONMENT = 'Test_Environment' 
        PRODUCTION_ENVIRONMENT = 'Paul_Eccarius'
    }

    tools {
        maven 'Maven 3.9.9' // Ensure this matches your Maven tool installation name
    }

    stages {
        stage('0 Delay') {
            steps {
                sleep 5
            }
        }
        
        stage('1 Build') {
            steps {
                echo "fetch the source code from the directory path specified by the environment variable"
                checkout scm
                echo "compile the code and generate any necessary artifacts"
                bat 'mvn clean compile' // Use bat instead of sh for Windows
            }
        }

        stage('2 Test') {
            steps {
                echo "Running unit tests and integration tests"
                bat 'mvn test' // Use bat instead of sh
                junit '**/target/surefire-reports/*.xml'
            }
        }

        stage('3 Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
                bat 'pmd.bat -d src -R rulesets/java/basic.xml -f xml > pmd_report.xml' // Adjust for PMD on Windows
                pmd canRunOnFailed: true, healthReportAmplificationFactor: 1.0, pattern: 'pmd_report.xml'
            }
        }

        stage('4 Security Scan') {
            steps {
                echo "Performing security scan"
                bat 'dependency-check.bat --project "hello-world" --scan ./ --out ./ --format XML' // Adjust for Dependency Check on Windows
                dependencyCheckPublisher canRunOnFailed: true, pattern: 'dependency-check-report.xml'
            }
        }

        stage('5 Deploy') {
            steps {
                echo "Deploying the application to a testing environment"
                // Add deployment commands specific to your setup here (e.g., SCP, SSH, etc.)
            }
        }

        stage('6 Integration Test') {
            steps {
                echo "Running integration tests on the staging environment"
                bat 'mvn integration-test' // Use bat instead of sh
            }
        }

        stage('7 Deploy to Production') {
            steps {
                echo "Deploying to production environment: ${env.PRODUCTION_ENVIRONMENT}"
                // Add production deployment commands here
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
