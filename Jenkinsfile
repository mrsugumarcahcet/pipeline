pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git(
                    branch: 'main',
                    url: 'https://github.com/mrsugumarcahcet/pipeline.git'
                )
            }
        }

        stage('Validate HTML') {
            steps {
                sh '''
                    if [ ! -f one.html ]; then
                        echo "❌ one.html not found!"
                        exit 1
                    fi
                    echo "✅ HTML validation passed"
                '''
            }
        }

        stage('Archive HTML Report') {
            steps {
                archiveArtifacts artifacts: 'one.html', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline executed successfully!'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
