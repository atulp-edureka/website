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
                ansiblePlaybook credentialsId: 'root', installation: 'myansible', playbook: 'devops/prerequisite.yaml' 
            }
        }
        stage('Deploy Project On Test Server') {
            steps {
                ansiblePlaybook credentialsId: 'root', installation: 'myansible', playbook: 'devops/deploy.yaml' 
            }
        }
        stage('Test website') {
            steps {
                sh 'python devops/checksiteisup.py'
            }
        }
        stage('Cleanup Test Server') {
            steps {
                ansiblePlaybook credentialsId: 'root', installation: 'myansible', playbook: 'devops/cleanup.yaml'
                //echo 'Cleaup all data from test server'
            }
        }
    }
}
