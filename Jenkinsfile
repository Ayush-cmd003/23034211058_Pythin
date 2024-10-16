pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Replace with your actual repository URL
                git 'https://github.com/Ayush-cmd003/23034211058_Pythin'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Check if requirements.txt exists before trying to install dependencies
                script {
                    if (fileExists('requirements.txt')) {
                        sh 'pip install -r requirements.txt'
                    } else {
                        echo 'No requirements.txt file found, skipping dependency installation.'
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Check if pytest is installed and if there are any tests
                script {
                    if (fileExists('tests') && fileExists('pytest')) {
                        sh 'pytest'
                    } else {
                        echo 'No tests found, skipping test stage.'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application'
                // You can add deployment steps here (e.g., copying files, starting services, etc.)
            }
        }
    }
}
