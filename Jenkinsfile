pipeline {
    agent any

    stages {
        stage('Run Postman Tests') {
            steps {
                sh '''
                    newman run collections/happy-path.postman_collection \
                        -e environments/"Postman-Course Env.postman_environment" \
                        --reporters cli,htmlextra \
                        --reporter-htmlextra-export newman-report.html
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'newman-report.html'
        }
    }
}