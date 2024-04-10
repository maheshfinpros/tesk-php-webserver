pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub using credentials with ID 'github-mahesh'
                git credentialsId: 'github-mahesh', url: 'https://github.com/maheshfinpros/tesk-php-webserver.git'
            }
        }
        
        stage('Deploy Code') {
            when {
                // Run this stage only if there are changes in the GitHub repository
                changeset 'github-mahesh'
            }
            steps {
                // Deploy code using rsync
                sshagent(credentials: ['new-ssh-ubuntu']) {
                    sh 'rsync -avz -e ssh /var/lib/jenkins/workspace/php=mahesh/ ubuntu@13.201.192.130:/var/www/html/'
                }
            }
        }
    }
}
