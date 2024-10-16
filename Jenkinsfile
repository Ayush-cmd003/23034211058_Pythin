pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Ayush-cmd003/23034211058_Python.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Skip if there's no requirements.txt, this won't cause an error
                script {
                    if (fileExists('requirements.txt')) {
                        sh 'pip install -r requirements.txt'
                    } else {
                        echo "No requirements.txt file found, skipping dependency installation."
                    }
                }
            }
        }

        stage('Run Application') {
            steps {
                // Run the Python script and print its output to the console
                sh 'python data.py'
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    if (fileExists('test_data.py')) {
                        sh 'pytest'
                    } else {
                        echo "No tests found, skipping test stage."
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application'
            }
        }
    }
}
