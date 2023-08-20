pipeline {
    agent any
    
    stages {

        stage('Delete Existing Directory') {
            steps {
                sh 'rm -rf DevSecOps'
    }
}

        stage('Clone Repository') {
            steps {
                // Clone your repository
                sh 'git clone https://github.com/shubnimkar/DevSecOps.git'
            }
        }
        
        stage('Run TruffleHog') {
            steps {
                dir('DevSecOps')
                {
                    // Change to the cloned repository directory
                    // Example: dir('my-repo')

                    // Install TruffleHog dependencies (if not already installed)
                    //sh 'pip3 install truffleHog'

                    // Run TruffleHog
                    sh 'trufflehog3 . '
                }
            }
        }
    }
}
