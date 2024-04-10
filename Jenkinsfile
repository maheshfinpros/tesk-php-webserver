pipeline {
    agent any
    stages {
        stage('Deploy Code to Same Server') {
            steps {
                script {
                    // Deploy code using rsync to the same server for index.html
                    sh 'rsync -avz /var/lib/jenkins/workspace/php=mahesh/index.html /var/www/html/'

                    // Deploy code using rsync to the same server for index.php
                    sh 'rsync -avz /var/lib/jenkins/workspace/php=mahesh/index.php /var/www/html/'
                }
            }
        }
        stage('Deploy Code to Remote Server') {
            when {
                changeset 'github'
            }
            steps {
                sshagent(credentials: ['new-ssh-ubuntu']) {
                    script {
                        // Deploy code using rsync to the remote server
                        sh 'rsync -avz -e ssh /var/lib/jenkins/workspace/php=mahesh/ ubuntu@13.201.192.130:/var/www/html/'

                        // Copy index.php to the web server directory
                        sh 'cp /var/lib/jenkins/workspace/php=mahesh/index.php /var/www/html/'

                        // Copy index.html to the web server directory
                        sh 'cp /var/lib/jenkins/workspace/php=mahesh/index.html /var/www/html/'
                    }
                }
            }
        }
    }
}
