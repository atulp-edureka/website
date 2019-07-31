pipeline {
    agent any
    stages {
        stage('Get devops repo from github') {
            steps {
                deleteDir()
                sh 'git clone https://github.com/atulp-edureka/devops.git'
            }
        }
        stage('Install Prerequisite [Docker dependencies and Docker]') {
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
