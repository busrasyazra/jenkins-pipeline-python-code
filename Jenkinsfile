pipeline {
    agent any
    stages {
        stage('run') {
            steps {
                echo 'Clarusway_Way to Reinvent Yourself....'
                sh 'python --version'
                sh 'python pipeline.py'
            }
        }
        stage("Test changeset"){
            when { 
                changeset "UPDATED_PATH"
            }
            steps {
                echo "The changeset test worked!!"
            }
        }
    }
}
