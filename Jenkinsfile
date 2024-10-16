pipeline {
    agent any

    stages {
        stage('Clone Repository') {
    steps {
        git branch: 'main', url: 'https://github.com/Ayush-cmd003/23034211058_Pythin.git'
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
                // Run the application and output the results
                sh 'python data.py > output.txt'
                echo 'Deploying Application'
                // You can add deployment steps here (e.g., copying files, starting services, etc.)
            }
        }
        stage('Display Output') {
            steps {
                // Display the contents of the output file in the console
                sh 'cat output.txt'
            }
        }
        stage('Archive Output') {
            steps {
                // Archive the output file so it can be downloaded from the Jenkins interface
                archiveArtifacts artifacts: 'output.txt', allowEmptyArchive: true
            }
        }
    }
}
