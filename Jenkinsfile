pipeline {
    agent any

    stages {
        stage('Hello World') {
            steps {
                echo 'Hello World'[cite: 2]
            }
        }

        stage('Run Script') {
            steps {
                sh '''
                    chmod +x hello.sh
                    ./hello.sh
                '''[cite: 2]
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished (success, failure, or aborted).'[cite: 2]
        }

        success {
            echo 'Pipeline executed successfully!'[cite: 2]
        }

        failure {
            echo 'Pipeline failed! Sending email...'
            emailext (
                subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                    <p>Check console output at <a href="${env.BUILD_URL}">${env.BUILD_URL}</a> to view the logs.</p>""",
                to: 'abdelazizamer03@gmail.com'
            )
        }

        aborted {
            echo 'Pipeline was aborted!'[cite: 2]
        }
    }
}
