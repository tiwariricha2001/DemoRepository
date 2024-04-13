pipeline {
    agent any
    tools {
        maven "MAVEN_HOME"
    }
    stages {
        stage('Build') {
            steps {
                // Clean and build the Maven project
                bat 'mvn -f demoProject/pom.xml clean package'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                bat 'mvn -f demoProject/pom.xml test'
            }
        }
        stage('Deploy') {
           steps {
               // Placeholder for deployment steps
              // Replace this with your deployment script or commands
               echo 'Deploying the application...'
            }
        }
        stage('Clean Up') {
            steps {
                // Clean up any temporary files or resources
                bat 'mvn -f demoProject/pom.xml clean'
            }
        }
    }
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
has context menu
