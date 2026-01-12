pipeline {
    agent { label 'windows' } // Jenkins Windows agent label
    

    options {
        timestamps()      // Adds timestamps to logs
    }

    stages {

        stage('Checkout Source Code') {
            steps {
                echo "🔄 Cloning GitHub repository..."
                git branch: 'main',
                    url: 'https://github.com/ReshmaArsh/jenkinsdemo.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Verify index.html') {
            steps {
                script {
                    echo "🔍 Checking for index.html..."

                    def result = bat(
                        script: '''
                        if exist index.html (
                            echo FOUND
                        ) else (
                            echo NOT_FOUND
                        )
                        ''',
                        returnStdout: true
                    ).trim()

                    if (result.contains('FOUND')) {
                        echo "✅ index.html found!"
                    } else {
                        error "❌ index.html not found in workspace!"
                    }
                }
            }
        }

        stage('Report Success') {
            steps {
                echo "🎉 Pipeline completed successfully on Windows!"
            }
        }
    }

    post {
        success {
            echo "✅ BUILD SUCCESSFUL"
        }
        failure {
            echo "❌ BUILD FAILED"
        }
        always {
            echo "🧹 Pipeline finished (cleanup can go here)"
        }
    }
}
