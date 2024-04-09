pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clean workspace
                deleteDir()

                // Checkout code from Git
                git url: 'https://github.com/maheshfinpros/tesk-php-webserver.git'
            }
        }

        stage('Deploy Files') {
            agent {
                label '13.201.192.130'
            }
            steps {
                // Deploy PHP and HTML files to web server
                sh "ssh ubuntu@13.201.192.130 sudo cp -r /var/lib/jenkins/workspace/php=mahesh/* /var/www/html"
            }
        }
    }
}
