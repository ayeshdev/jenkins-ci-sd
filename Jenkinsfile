pipeline {
    agent any  // This means the job can run on any available Jenkins agent

    environment {
        // Define any environment variables you might need, such as Java Home
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64"
        MAVEN_HOME = "/usr/share/maven" // If Maven is installed in a custom path
        PATH = "${MAVEN_HOME}/bin:${env.PATH}" // Ensure Maven is available in the path
    }

    stages {
        stage('Checkout') {
            steps {
                // Step to checkout the code from the GitHub repository
                git branch: 'master', url: 'https://github.com/ayeshdev/jenkins-ci-sd.git'
            }
        }

        stage('Build') {
            steps {
                // Step to build the Spring Boot application using Maven
                script {
                    // Run Maven clean package without tests (if desired)
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Test') {
            steps {
                // Step to run tests for the Spring Boot application
                script {
                    // Run the tests using Maven
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Step to deploy the application (you can customize this for your needs)
                echo "Deploying application to the server"
                // Example of deploying to a remote server:
                // sh 'scp target/my-app.jar user@server:/path/to/deploy'
                // Or use your deployment tool/steps
            }
        }
    }

    post {
        success {
            // Actions to take if the build and tests are successful
            echo "Build and tests were successful!"
            // You can notify a Slack channel or send an email here
        }
        failure {
            // Actions to take if the build or tests fail
            echo "Build failed! Check the logs for more details."
            // You can also notify on failure, send failure reports, etc.
        }
    }
}
