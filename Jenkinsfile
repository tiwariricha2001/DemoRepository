pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Use Maven to build the application
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Set up the environment (e.g., download dependencies, set up WebDriver)
                bat 'choco install selenium-all-drivers -y' // Install Selenium WebDriver via Chocolatey
                bat 'choco install chromedriver -y' // Install ChromeDriver via Chocolatey
                
                // Run the test class with TestNG
                bat 'mvn test -Dtest=AmazonWebsiteTest'
            }
            post {
                // Fail the pipeline if any tests fail
                failure {
                    echo 'Tests failed! Pipeline will fail.'
                    currentBuild.result = 'FAILED'
                }
            }
        }
    }

    // Automatically trigger the pipeline whenever changes are pushed to the repository
    triggers {
        scm('*/5 * * * *') // Poll SCM every 5 minutes (adjust as needed)
    }
}
