pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
    parameters {
        choice(name: 'CHOICE', choices: ['init', 'apply', 'destroy'], description: 'Choose one')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    if (${params.CHOICE} == 'init') {
                        sh 'cd Infrastructure/ && terraform init'
                    } if (${params.CHOICE} == 'apply') {
                        sh 'cd Infrastructure/ && terraform apply -auto-approve'
                    } else {
                        sh 'cd Infrastructure/ && terraform destroy -auto-approve'
                    }
                }
            }
        }
    }
}
