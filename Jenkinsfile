pipeline {
    agent any
    stages {
        stage('Install Prerequisite [docker dependencies and docker]') {
            steps {
                sh 'ansible-playbook /root/devops/prerequisite.yaml' 
            }
        }
        stage('Deploy Project On Test Server') {
            steps {
                sh 'ansible-playbook /root/devops/deploy.yaml' 
            }
        }
        stage('Test website') {
            steps {
                echo 'Testing Done'
            }
        }
        stage('Cleanup Test Server') {
            steps {
                //sh 'ansible-playbook /root/devops/deploy.yaml'
                echo 'Cleaup all data from test server'
            }
        }
    }
}
