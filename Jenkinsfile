pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository code
                git url: 'https://github.com/wissam-elhajj/devops.git', branch: 'master'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js dependencies if working with an Angular project
                    bat  'npm install'
					bat  'npm install @angular-devkit/build-angular --save-dev'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the Angular project
                    bat 'npm run build --prod'
                }
            }
        }

        stage('Deploy to IIS') {
            steps {
                script {
                    // Add the deployment step (could be via FTP, WebDeploy, etc.)
                    echo 'Deploying to IIS...'
                }
            }
        }
    }

    post {
        always {
            // Clean up after the pipeline finishes
            echo 'Cleaning up...'
        }
    }
}
