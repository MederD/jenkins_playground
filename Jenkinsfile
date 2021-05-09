pipeline {
    parameters {
        choice(name: 'CHOICE', choices: ['init', 'apply', 'destroy'], description: 'Choose one')
    }

    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stages {
        stage('Example') {
            steps {
                sh "cd Infrastructure/ && terraform ${ params.CHOICE }"
            }
        }
    }
}
