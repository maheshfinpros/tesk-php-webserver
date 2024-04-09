pipeline {
    agent any
    stages {
        stage('Deploy Code') {
            when {
                changeset '**'  // Trigger the deployment for any changes in the repository
            }
            steps {
                sshagent(credentials: ['new-ssh-ubuntu']) { 
                    sh 'rsync -avz -e ssh /var/lib/jenkins/workspace/php-mahesh/ ubuntu@13.201.192.130:/var/www/html/'
                }
            }
        }
    }
}
