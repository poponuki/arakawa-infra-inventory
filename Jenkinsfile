pipeline {
    agent any

    stages {
        stage('Prepare') {
            steps {
                git 'https://github.com/poponuki/arakawa-infra-inventory.git'
            }
        }

        stage('Build ansible syntax check') {
            steps {
                sh 'sudo -u centos ansible-playbook --syntax-check -i ./inventory/hosts ./arakawa_deploy.yml'
            }
        }

        stage('Build ansible check') {
            steps {
                sh 'sudo -u centos ansible-playbook --check -i ./inventory/hosts ./arakawa_deploy.yml || true'
            }
        }

        stage('Build ansible playbook') {
            steps {
                sh 'sudo -u centos ansible-playbook -i ./inventory/hosts ./arakawa_deploy.yml'
            }
        }
    }
}
