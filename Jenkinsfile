pipeline {
    agent any

    environment {
        MAVEN_HOME = 'M2_HOME'  // Update this to your configured Maven version
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository from GitHub
                git branch: 'main', url: 'https://github.com/DevObed/maven-code.git'
            }
        }

        stage('Build and Package') {
            steps {
                // Run Maven clean, install, and package in one step
               sh  '/usr/bin/mvn clean install package'
            }
        }

        stage('Archive Artifact') {
            steps {
                // Archive the generated JAR/WAR for reference
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build and package completed successfully! ✅'
        }
        failure {
            echo 'Build failed! ❌ Check the logs for details.'
        }
    }
}
