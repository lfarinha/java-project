pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'ant -f test.xml -v'
            }
        }
        stage('Build') {
            steps {
                sh 'ant -f build.xml -v'
            }
        }
        stage('Deploy') {
            steps {
                sh 'aws s3 cp /workspace/JavaPipeline/dist/* s3://javaprojectbucket'
            }
        }
        stage('Report') {
            steps {
                echo 'Reporting....'
            }
        }
    }
}