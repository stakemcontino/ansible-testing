pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                checkout scm
                sh 'virtualenv venv'
                sh 'source venv/bin/activate'
                sh 'pip install ansible 'docker<3.0.0' molecule'
                sh 'deactivate'
            }
        }
        stage('Lint') {
            steps {
                echo 'Testing...'
                sh 'source venv/bin/activate'
                sh 'molecule lint'
            }
        }
        stage('Create') {
            steps {
                echo 'Creating docker instance....'
                sh 'source venv/bin/activate'
                sh 'molecule create'
            }
        }
        stage('Converge') {
            steps {
                echo 'Converge playbook to docker instance...'
                sh 'mkdir molecule/default/roles'
                sh 'cd molecule/default/roles'
                sh 'git clone https://github.com/stakemcontino/ansible-testing.git'
                sh 'molecule converge'
            }
        }
    }
}
