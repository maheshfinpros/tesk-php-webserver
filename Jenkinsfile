pipeline {
    agent any
    stages {
        stage('Deploy Code') {
            when {
                changeset 'github'
            }
            steps {
                sshagent(['new-ssh-ubuntu']) { 
                    sh 'rsync -avz -e ssh /var/lib/jenkins/workspace/php=mahesh/ ubuntu@13.201.192.130:/var/www/html/'
                }
            }
        }
    }
}
