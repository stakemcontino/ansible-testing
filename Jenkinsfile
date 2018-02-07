pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                checkout scm
            }
        }
        stage('Lint') {
            steps {
                echo 'Testing...'
                sh 'molecule lint'
            }
        }
        stage('Create') {
            steps {
                echo 'Creating docker instance....'
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
