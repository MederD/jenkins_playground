pipeline {
    parameters {
        string(name: 'INIT', defaultValue: 'init', description: 'teraform init?')
    }
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stages {
        stage('Init') {
            steps {
                sh "cd Infrastructure/ && terraform ${ params.INIT }"
            }
        }
        stage('Apply') {
            steps {
                sh "cd Infrastructure/ && terraform ${ params.INIT }"
            }
        }
    }
}
