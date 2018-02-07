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
    }
}
