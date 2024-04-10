pipeline {
    agent any
    stages {
        stage('Deploy Code') {
            when {
                changeset 'github'
            }
            steps {
                sshagent(credentials: ['new-ssh-ubuntu']) {
                    script {
                        // Deploy code using rsync
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
