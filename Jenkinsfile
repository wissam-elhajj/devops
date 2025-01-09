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
                // Run npm install to install Angular dependencies
                bat 'npm install'
            }
        }

        stage('Build Angular App') {
            steps {
                // Run the build command for Angular in production mode
                bat 'npm run build --prod'
            }
        }
		
		stage('Archive Build Files') {
            steps {
                // Copy build output (dist folder) to an artifacts folder
                bat 'mkdir build-artifacts'
                bat 'xcopy /E /I /H /Y dist\\* build-artifacts\\'
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
		success {
            echo 'Build and Deploy pipeline succeeded!'
        }
        always {
            // Clean up after the pipeline finishes
            echo 'Cleaning up...'
        }
		failure {
            echo 'Build and Deploy pipeline failed!'
        }
    }
}
