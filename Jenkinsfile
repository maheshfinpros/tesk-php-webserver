pipeline {
    agent any
    stages {
        stage('Deploy Code') {
            steps {
                sshagent(['ubuntu-ssh']) { 
                    sh 'rsync -avz -e ssh /var/lib/jenkins/workspace/php=mahesh/ ubuntu@13.201.192.130:/var/www/html/'
                }
            }
        }
    }
}
