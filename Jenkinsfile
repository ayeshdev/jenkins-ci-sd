pipeline {
    agent any  // This means the job can run on any available Jenkins agent

    environment {
        // Define any environment variables you might need, such as Java Home
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64"
    }

    stages {
        stage('Checkout') {
            steps {
                // Step to checkout the code from the GitHub repository
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                // Step to build the Spring Boot application using Maven
                script {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Test') {
            steps {
                // Step to run tests for the Spring Boot application
                script {
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Step to deploy the application (you can customize this for your needs)
                echo "Deploying application to the server"
                // Example: sh 'deploy.sh' (if you have a deploy script for example)
            }
        }
    }

    post {
        success {
            // Actions to take if the build and tests are successful
            echo "Build and tests were successful!"
        }
        failure {
            // Actions to take if the build or tests fail
            echo "Build failed! Check the logs for more details."
        }
    }
}
