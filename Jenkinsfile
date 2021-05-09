pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stages {
        stage('Release scope') {
            steps {
                script {
                    // Prepare a list and write to file
                    sh "echo \"init\napply\ndestroy\" > ${WORKSPACE}/list"

                    // Load the list into a variable
                    env.LIST = readFile (file: "${WORKSPACE}/list")

                    // Show the select input
                    env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                            parameters: [choice(name: 'RELEASE_SCOPE', choices: env.LIST, description: 'What is the release scope?')]
                }
                sh "cd Infrastructure/ && terraform ${env.RELEASE_SCOPE}"
            }
        }
    }
}
