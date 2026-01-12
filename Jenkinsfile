pipeline {
    agent { label 'windows' } // Ensure Jenkins agent is Windows

    stages {
        stage('Clone Repository') {
            steps {
                // Replace with your repo URL
                git branch: 'main', url: 'https://github.com/ReshmaArsh/jenkinsdemo.git'
            }
        }

        stage('Verify index.html') {
            steps {
                script {
                    // PowerShell command to check file existence
                    def fileExists = bat(script: 'if exist index.html (echo true) else (echo false)', returnStdout: true).trim()
                    
                    if (fileExists == 'true') {
                        echo "✅ index.html found!"
                    } else {
                        error "❌ index.html not found!"
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
}
