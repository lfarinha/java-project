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
                sh 'serverless config credentials --provider aws --key  AKIATGKM2XWEDQFRWTP4 --secret 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'
                sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
            }
        }
    }
}