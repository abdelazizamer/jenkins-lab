pipeline {
    agent any

    stages {
        stage('Hello World') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Fail Purposefully') {
            steps {
                sh 'exit 1'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed! Sending email...'
            emailext (
                subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                    <p>Check console output at <a href="${env.BUILD_URL}">${env.BUILD_URL}</a> to view the logs.</p>""",
                to: 'abdelazizamer03@gmail.com'
            )
        }
    }
}
